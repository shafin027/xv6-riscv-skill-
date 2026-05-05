# Example: Adding a New System Call

This example demonstrates how to add a new system call `settickets` to xv6-riscv.

## Step-by-Step Implementation

### 1. Add syscall number (`kernel/syscall.h`)

```c
#define SYS_settickets 22
```

### 2. Add to syscall table (`kernel/syscall.c`)

```c
// In the extern declarations section:
extern uint64 sys_settickets(void);

// In the syscalls[] array:
[SYS_settickets] sys_settickets,
```

### 3. Implement the syscall (`kernel/sysproc.c`)

```c
uint64
sys_settickets(void)
{
  int n;
  struct proc *p;

  argint(0, &n);
  if(n <= 0)
    return -1;

  p = myproc();
  acquire(&p->lock);
  p->tickets = n;
  release(&p->lock);

  return 0;
}
```

### 4. Add user-space prototype (`user/user.h`)

```c
int settickets(int);
```

### 5. Add syscall stub (`user/usys.pl`)

```perl
entry("settickets");
```

### 6. Rebuild and test

```bash
make clean
make qemu
```

Inside xv6:
```bash
$ settickets 10
```

## Common Mistakes

- ❌ Forgetting to add entry to `usys.pl` → "undefined reference"
- ❌ Forgetting to add prototype to `user/user.h` → compilation error
- ❌ Not holding `p->lock` when modifying process fields → race condition
- ❌ Wrong syscall number in `syscall.h` → "unknown sys call"
