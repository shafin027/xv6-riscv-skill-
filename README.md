# xv6-riscv-expert

> Claude Code Skill for solving, implementing, debugging, and explaining MIT-style xv6 on 64-bit RISC-V.

<p align="center">
  <a href="https://skills.sh/shafin027/xv6-riscv-skill">
    <img alt="Install Skill" src="https://img.shields.io/badge/Install%20Skill-Click%20Here-7c3aed?style=for-the-badge">
  </a>
  <a href="https://github.com/shafin027/xv6-riscv-skill">
    <img alt="Repository" src="https://img.shields.io/badge/GitHub-xv6--riscv--skill-181717?style=for-the-badge&logo=github">
  </a>
</p>

<p align="center">
  <img alt="Stars" src="https://img.shields.io/github/stars/shafin027/xv6-riscv-skill?style=for-the-badge&logo=github">
  <img alt="Forks" src="https://img.shields.io/github/forks/shafin027/xv6-riscv-skill?style=for-the-badge&logo=github">
  <img alt="Watchers" src="https://img.shields.io/github/watchers/shafin027/xv6-riscv-skill?style=for-the-badge&logo=github">
  <img alt="Issues" src="https://img.shields.io/github/issues/shafin027/xv6-riscv-skill?style=for-the-badge">
  <img alt="License" src="https://img.shields.io/github/license/shafin027/xv6-riscv-skill?style=for-the-badge">
  <img alt="Last Commit" src="https://img.shields.io/github/last-commit/shafin027/xv6-riscv-skill?style=for-the-badge">
</p>

<p align="center">
  <a href="https://github.com/shafin027/xv6-riscv-skill">
    <img alt="Repository Card" src="https://github-readme-stats.vercel.app/api/pin/?username=shafin027&repo=xv6-riscv-skill&theme=radical&hide_border=true&cache_seconds=21600">
  </a>
</p>

---

## What this skill does

`xv6-riscv-expert` turns Claude Code into a focused assistant for xv6-riscv operating-system assignments. It is designed for students working with MIT xv6-riscv and SNU's xv6-riscv-snu fork.

It helps with:

- system calls
- scheduler changes
- virtual memory and page tables
- traps, interrupts, and page faults
- process lifecycle logic
- locks and race conditions
- file-system assignments
- xv6 debugging with QEMU and GDB

---

## Quick install

### Option 1: Install with skills CLI

```bash
npx skills add shafin027/xv6-riscv-skill
```

### Option 2: Manual install

```bash
git clone https://github.com/shafin027/xv6-riscv-skill.git ~/.claude/skills/xv6-riscv-expert
```

### Option 3: Install locally inside a project

```bash
cd /path/to/your/project
npx skills add shafin027/xv6-riscv-skill --local
```

---

## Usage

### Slash command

```text
/xv6-riscv-expert
```

### Natural trigger examples

```text
I need to add a new syscall to xv6-riscv.
```

```text
Help me debug this xv6 trap: scause=15, sepc=..., stval=...
```

```text
Implement lottery scheduling in xv6-riscv.
```

---

## Supported assignment types

| Area | Examples |
|---|---|
| System calls | `trace`, `sysinfo`, `settickets`, custom syscall wiring |
| Scheduling | lottery scheduler, priority scheduler, round-robin changes |
| Virtual memory | `vmprint`, page-table walking, PTE flags, USYSCALL, COW fork |
| Traps | `usertrap`, `kerneltrap`, `scause`, `sepc`, `stval` debugging |
| Processes | `fork`, `exit`, `wait`, `sleep`, `wakeup`, process states |
| Locks | spinlocks, sleeplocks, deadlock/race debugging |
| File system | inodes, log, buffer cache, large file support |
| Boot/init | kernel startup, QEMU boot flow, init process |

---

## Example workflows

### Add a syscall

Prompt:

```text
Add a syscall called settickets(int n) to xv6-riscv.
```

The skill will usually produce:

1. files to modify
2. exact code patches
3. syscall-number wiring
4. user-space wrapper changes
5. test program
6. common mistakes
7. `make qemu` validation steps

### Debug a page fault

Prompt:

```text
My xv6 kernel panics with scause=15 inside sys_write.
```

The skill will focus on:

- whether the fault is load/store/instruction related
- `stval` fault address
- `sepc` faulting instruction
- user pointer validation
- `copyin` / `copyout`
- PTE permissions

### Build a scheduler assignment

Prompt:

```text
Implement lottery scheduler with process tickets.
```

The skill will guide changes in:

- `kernel/proc.h`
- `kernel/proc.c`
- `kernel/sysproc.c`
- syscall glue files
- user-level test files

---

## xv6-riscv setup

### Ubuntu/Debian prerequisites

```bash
sudo apt update
sudo apt install git build-essential gdb-multiarch qemu-system-misc \
                 gcc-riscv64-linux-gnu binutils-riscv64-linux-gnu
```

### Clone xv6-riscv

```bash
git clone https://github.com/mit-pdos/xv6-riscv.git
cd xv6-riscv
```

### Build and run

```bash
make clean
make qemu
```

### Debug with GDB

Terminal 1:

```bash
make qemu-gdb
```

Terminal 2:

```bash
gdb-multiarch kernel/kernel
```

Inside GDB:

```gdb
target remote localhost:26000
b syscall
b usertrap
c
```

---

## Skill knowledge base

The skill includes practical knowledge for:

- xv6 file map
- syscall implementation checklist
- RISC-V calling convention
- trap debugging process
- Sv39 page-table reasoning
- kernel/user memory boundary rules
- process-state transitions
- scheduler lock discipline
- GDB debugging commands
- patch-file creation

---

## Common xv6 mistakes this skill catches

- adding a syscall in `sysproc.c` but forgetting `user/user.h`
- forgetting to update `user/usys.pl`
- using a raw user pointer directly inside the kernel
- forgetting `copyin`, `copyout`, or `argaddr`
- modifying process fields without holding `p->lock`
- breaking scheduler lock order
- printing too much inside timer interrupt paths
- assuming virtual addresses equal physical addresses
- forgetting to add user test programs to `UPROGS`

---

## Assignment checklist

- [ ] Identify the assignment category
- [ ] Locate the right kernel/user files
- [ ] Make the smallest correct change
- [ ] Compile with `make clean && make qemu`
- [ ] Test normal cases
- [ ] Test edge cases
- [ ] Check for panics, deadlocks, and infinite loops
- [ ] Create final patch if required

```bash
git diff > xv6-solution.patch
```

---

## Repository health

This README intentionally uses stable Shields.io badges and the correct GitHub Readme Stats endpoint for a repository card:

```text
https://github-readme-stats.vercel.app/api/pin/?username=shafin027&repo=xv6-riscv-skill
```

Do not use this broken form for repository stats:

```text
https://github-readme-stats.vercel.app/api?username=shafin027&repo=xv6-riscv-skill
```

That endpoint is for user profile stats, not repo-card stats.

---

## Resources

- [MIT xv6-riscv](https://github.com/mit-pdos/xv6-riscv)
- [xv6 book](https://pdos.csail.mit.edu/6.828/2020/xv6-book.html)
- [SNU xv6-riscv-snu](https://github.com/snu-csl/xv6-riscv-snu)
- [RISC-V specifications](https://riscv.org/technical/specifications/)

---

## Contributing

Pull requests are welcome.

```bash
git checkout -b feature/improve-skill
git add .
git commit -m "Improve xv6 skill docs"
git push origin feature/improve-skill
```

Then open a pull request.

---

## License

MIT License.

---

<p align="center">
  Built for OS students who are tired of vague xv6 explanations.
</p>
