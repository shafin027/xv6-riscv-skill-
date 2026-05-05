# Example: Lottery Scheduler#

This example shows how to implement a lottery scheduler in xv6-riscv.

## Overview#

Replace the default round-robin scheduler with a lottery scheduler where:
- Each process has a certain number of **tickets**
- A random number is drawn to select the winning process
- Process with T tickets gets ~T/total_tickets CPU time

## Implementation Steps#

### 1. Add fields to `struct proc` (`kernel/proc.h`)

```c
struct proc {
  // ... existing fields ...
  int tickets;  // Number of tickets for lottery scheduling
  int rounds;   // Number of rounds this process has run
};
```

### 2. Initialize in `allocproc()` (`kernel/proc.c`)

```c
found:
  p->pid = allocproc();
  p->state = USED;
  p->tickets = 1;  // Default: 1 ticket
  p->rounds = 0;     // Initial rounds is 0
```

### 3. Set init process tickets in `userinit()` 

```c
void
userinit(void)
{
  struct proc *p;

  p = allocproc();
  initproc = p;

  p->cwd = namei("/");
  
  p->tickets = 10;  // Init process gets 10 tickets

  p->state = RUNNABLE;

  release(&p->lock);
}
```

### 4. Inherit tickets in `kfork()` (`kernel/proc.c`)

```c
// In kfork(), after copying other fields:
np->tickets = p->tickets;  // Inherit from parent
```

### 5. Implement random number generator (`kernel/proc.c`)

```c
int do_rand(unsigned long *ctx) {
    long hi, lo, x;
    
    x = (*ctx % 0x7ffffffe) + 1;
    hi = x / 127773;
    lo = x % 127773;
    x = 16807 * lo - 2836 * hi;
    if (x < 0)
        x += 0x7fffffff;
    x--;
    *ctx = x;
    return (x);
}

unsigned long rand_next = 1;

int rand(void) {
    return (do_rand(&rand_next));
}
```

### 6. Replace scheduler with lottery algorithm (`kernel/proc.c`)

```c
void
scheduler(void)
{
  struct proc *p;
  struct cpu *c = mycpu();
  int total_tickets;
  int winning_ticket;
  int ticket_sum;

  c->proc = 0;
  for(;;){
    intr_on();
    intr_off();

    // First pass: calculate total tickets
    total_tickets = 0;
    for(p = proc; p < &proc[NPROC]; p++) {
      acquire(&p->lock);
      if(p->state == RUNNABLE) {
        total_tickets += p->tickets;
      }
      release(&p->lock);
    }

    if(total_tickets == 0) {
      asm volatile("wfi");
      continue;
    }

    // Generate winning ticket
    winning_ticket = rand() % total_tickets;

    // Second pass: find the process with the winning ticket
    ticket_sum = 0;
    for(p = proc; p < &proc[NPROCS]; p++) {
      acquire(&p->lock);
      if(p->state == RUNNABLE) {
        ticket_sum += p->tickets;
        if(ticket_sum > winning_ticket) {
          p->state = RUNNING;
          p->rounds++;  // Increment rounds counter
          c->proc = p;
          swtch(&c->context, &p->context);

          c->proc = 0;
          release(&p->lock);
          break;
        }
      }
      release(&p->lock);
    }
  }
}
```

### 7. Update `procdump()` to show rounds (`kernel/proc.c`)

```c
// In procdump(), change the printf line to:
printf("%d %s %s %d %d", p->pid, state, p->name, p->tickets, p->rounds);
```

### 8. Create test program (`user/test_scheduler.c`)

```c
#include "kernel/types.h"
#include "kernel/stat.h"
#include "user/user.h"

int
main(int argc, char *argv[])
{
  int tickets;

  if(argc != 2){
    printf("Usage: test_scheduler <ticket_count>\n");
    exit(1);
  }

  tickets = atoi(argv[1]);
  if(settickets(tickets) < 0){
    printf("settickets failed\n");
    exit(1);
  }

  // Spin forever
  for(;;){
    // Do nothing, just spin
  }

  exit(0);
}
```

### 9. Update Makefile#

Add to UPROGS:
```
$U/_test_scheduler\
```

Set CPUS := 1 (single-CPU for proper behavior)

### 10. Test#

```bash
make clean
make qemu
```

Inside xv6:
```bash
$ test_scheduler 10 &
$ test_scheduler 5 &
$ test_scheduler 2 &
```

Press `Ctrl+P` multiple times to see rounds.

## Expected Behavior#

- Process with 10 tickets should get ~50% CPU time
- Process with 5 tickets should get ~25% CPU time
- Process with 2 tickets should get ~10% CPU time
- Rounds should converge to ticket ratios over time

## Common Mistakes#

- ❌ Forgetting to set CPUS := 1 → scheduler behaves incorrectly
- ❌ Not calculating total_tickets before drawing → division by zero
- ❌ Not holding p->lock when reading/writing process fields → race condition
- ❌ Wrong ticket_sum comparison (>= vs >) → process never wins
- ❌ Not breaking after finding winner → multiple processes run
