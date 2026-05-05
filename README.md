# xv6-riscv-expert

> Claude Code Skill for solving, implementing, debugging, and explaining xv6-riscv operating system assignments on 64-bit RISC-V.

<p align="center">
  <a href="https://skills.sh/shafin027/xv6-riscv-skill">
    <img src="https://img.shields.io/badge/Install%20Skill-Click%20Here-purple?style=for-the-badge" alt="Install Skill">
  </a>
  <a href="https://github.com/shafin027/xv6-riscv-skill/stargazers">
    <img src="https://img.shields.io/github/stars/shafin027/xv6-riscv-skill?style=for-the-badge&color=yellow" alt="GitHub stars">
  </a>
  <a href="https://github.com/shafin027/xv6-riscv-skill/network/members">
    <img src="https://img.shields.io/github/forks/shafin027/xv6-riscv-skill?style=for-the-badge&color=blueviolet" alt="GitHub forks">
  </a>
  <a href="https://github.com/shafin027/xv6-riscv-skill/issues">
    <img src="https://img.shields.io/github/issues/shafin027/xv6-riscv-skill?style=for-the-badge&color=red" alt="GitHub issues">
  </a>
  <a href="LICENSE">
    <img src="https://img.shields.io/github/license/shafin027/xv6-riscv-skill?style=for-the-badge&color=green" alt="License">
  </a>
</p>

---

## Overview

`xv6-riscv-expert` is a Claude Code skill designed for students and developers working with MIT-style `xv6-riscv` and SNU's `xv6-riscv-snu` operating system assignments.

It helps with:

- implementing system calls
- modifying the scheduler
- debugging traps and page faults
- understanding RISC-V registers
- working with page tables and virtual memory
- modifying process management code
- handling locks and concurrency
- explaining xv6 concepts in exam-friendly language
- writing clean xv6-style C code

This is not a generic OS prompt. It is built specifically around the xv6 RISC-V codebase and the kinds of assignments students usually face.

---

## Repository Stats

<p align="center">
  <img src="https://img.shields.io/github/stars/shafin027/xv6-riscv-skill?label=Stars&style=for-the-badge&color=yellow" alt="Stars">
  <img src="https://img.shields.io/github/forks/shafin027/xv6-riscv-skill?label=Forks&style=for-the-badge&color=blueviolet" alt="Forks">
  <img src="https://img.shields.io/github/watchers/shafin027/xv6-riscv-skill?label=Watchers&style=for-the-badge&color=informational" alt="Watchers">
  <img src="https://img.shields.io/github/issues/shafin027/xv6-riscv-skill?label=Issues&style=for-the-badge&color=red" alt="Issues">
</p>

<!--
Optional repository card.
If this does not render, keep it commented out. GitHub Readme Stats can fail because of Vercel rate limits, GitHub API limits, or cache delays.

[![Repo Card](https://github-readme-stats.vercel.app/api/pin/?username=shafin027&repo=xv6-riscv-skill&theme=radical&show_owner=true&cache_seconds=86400)](https://github.com/shafin027/xv6-riscv-skill)
-->

---

## Quick Install

### Option 1: Install with Skills CLI

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

## Skill Metadata

The skill uses this Claude Code skill structure:

```yaml
---
name: xv6-riscv-expert
description: Expert knowledge on MIT-style xv6 operating system assignments for 64-bit RISC-V. Helps implement, debug, and explain syscalls, schedulers, traps, page tables, process management, file systems, and kernel code.
trigger: xv6
---
```

Expected folder structure:

```text
xv6-riscv-expert/
└── SKILL.md
```

---

## Usage

### Slash command

```text
/xv6-riscv-expert
```

### Automatic triggering

Claude Code should use the skill when you ask questions like:

```text
I need to add a new syscall to xv6-riscv.
```

```text
Debug this xv6 page fault: scause=15, stval=0x0.
```

```text
Help me implement a lottery scheduler in xv6-riscv.
```

```text
Explain usertrap and kerneltrap in xv6.
```

---

## Supported Assignment Types

| Area | Examples |
|---|---|
| System calls | `trace`, `settickets`, `getpinfo`, `sysinfo`, custom syscall implementation |
| Scheduler | lottery scheduler, priority scheduler, process accounting, `yield`, `sched`, `scheduler` |
| Virtual memory | Sv39 page tables, `walk`, `mappages`, `uvmalloc`, `copyin`, `copyout`, `vmprint` |
| Traps | `usertrap`, `kerneltrap`, `scause`, `sepc`, `stval`, timer interrupts, page faults |
| Process management | `fork`, `exit`, `wait`, `sleep`, `wakeup`, process states |
| Locks | spinlocks, sleeplocks, race conditions, deadlocks, interrupt disabling |
| File system | inodes, buffer cache, logging, file descriptors, large files |
| User programs | adding programs to `UPROGS`, editing `user.h`, generating syscall stubs |
| Debugging | QEMU, GDB, kernel panics, register inspection, backtraces |

---

## xv6 RISC-V File Map

| File | Purpose |
|---|---|
| `kernel/proc.c` | process lifecycle, scheduler, `fork`, `exit`, `wait`, `sleep`, `wakeup` |
| `kernel/proc.h` | `struct proc`, process states, process-related fields |
| `kernel/sysproc.c` | process-related syscall implementations |
| `kernel/syscall.c` | syscall dispatcher and syscall table |
| `kernel/syscall.h` | syscall numbers |
| `kernel/trap.c` | trap handling, interrupts, exceptions, system call entry path |
| `kernel/vm.c` | page tables, virtual memory, mapping, copying user memory |
| `kernel/riscv.h` | RISC-V registers, CSR helpers, PTE flags |
| `kernel/defs.h` | kernel function declarations |
| `kernel/spinlock.c` | spinlock implementation |
| `kernel/sleeplock.c` | sleeplock implementation |
| `kernel/file.c` | file table and file operations |
| `kernel/fs.c` | inode and file system logic |
| `user/user.h` | user-space function and syscall declarations |
| `user/usys.pl` | syscall stub generator |
| `Makefile` | build system and user program list |

---

## Common xv6 System Call Workflow

When adding a syscall, the skill should check these files:

1. Add syscall number in `kernel/syscall.h`
2. Add kernel function declaration in `kernel/defs.h` if needed
3. Implement syscall handler in `kernel/sysproc.c` or another suitable `sys*.c` file
4. Register handler in `kernel/syscall.c`
5. Add user declaration in `user/user.h`
6. Add syscall stub in `user/usys.pl`
7. Add a test program in `user/`
8. Add the test program to `UPROGS` in `Makefile`

Example test command:

```bash
make clean
make qemu
```

---

## Debugging Focus

For xv6 RISC-V bugs, the skill should prioritize:

- `scause`: why the trap happened
- `sepc`: where the trap happened
- `stval`: bad address or faulting value
- `a0` to `a7`: syscall arguments and return values
- `s0` to `s11`: callee-saved registers
- PTE flags: `PTE_V`, `PTE_R`, `PTE_W`, `PTE_X`, `PTE_U`
- process state transitions
- lock acquire/release order
- user pointer validation through `copyin`, `copyout`, and `copyinstr`

Useful commands:

```bash
make qemu
make qemu-gdb
riscv64-linux-gnu-gdb kernel/kernel
```

Inside GDB:

```gdb
b syscall
b usertrap
b panic
info registers
x/10i $sepc
bt
continue
```

---

## Example Prompts

### Add a syscall

```text
Use xv6-riscv-expert. Add a syscall called getreadcount() that returns how many times read() has been called.
```

### Debug a trap

```text
Use xv6-riscv-expert. My kernel panics with scause=13 and stval=0x0 after fork(). Find the likely bug.
```

### Explain page tables

```text
Use xv6-riscv-expert. Explain how walk(), mappages(), and copyout() work together in xv6-riscv.
```

### Implement scheduler

```text
Use xv6-riscv-expert. Implement a lottery scheduler with tickets and a test program.
```

---

## Expected Answer Style

The skill should answer xv6 questions using this structure:

1. Identify the exact xv6 subsystem involved
2. List every file that must be changed
3. Explain the logic before giving code
4. Provide minimal xv6-style C patches
5. Include test commands
6. Mention common mistakes
7. Explain the result in exam-friendly language when asked

The skill should avoid dumping random code without explaining where it goes.

---

## xv6 Setup

### Ubuntu/Debian

```bash
sudo apt update
sudo apt install git build-essential gdb-multiarch qemu-system-misc \
  gcc-riscv64-linux-gnu binutils-riscv64-linux-gnu
```

### Clone MIT xv6-riscv

```bash
git clone https://github.com/mit-pdos/xv6-riscv.git
cd xv6-riscv
make qemu
```

### Clone SNU xv6-riscv-snu

```bash
git clone https://github.com/snu-csl/xv6-riscv-snu.git
cd xv6-riscv-snu
make qemu
```

---

## Recommended Workflow for Assignments

```bash
git status
git checkout -b assignment-solution
make clean
make qemu
```

After implementation:

```bash
make clean
make qemu
```

Generate a patch:

```bash
git diff > solution.patch
```

Or for staged changes:

```bash
git add .
git diff --staged > solution.patch
```

---

## Troubleshooting README Badges

If a badge does not render:

1. Open the badge URL directly in the browser
2. Check whether the repository name is correct
3. Wait a few minutes for GitHub cache to refresh
4. Avoid depending on third-party dynamic repo cards for critical README content

This README intentionally uses stable `img.shields.io` badges for repository stats. The GitHub Readme Stats repository card is left commented out because it can fail because of API limits, Vercel cache problems, or temporary service downtime.

---

## Resources

- [MIT xv6-riscv](https://github.com/mit-pdos/xv6-riscv)
- [SNU xv6-riscv-snu](https://github.com/snu-csl/xv6-riscv-snu)
- [xv6 Book](https://pdos.csail.mit.edu/6.828/2020/xv6-book.html)
- [RISC-V Specifications](https://riscv.org/technical/specifications/)
- [Claude Code Skills Documentation](https://docs.anthropic.com/en/docs/claude-code/skills)

---

## Contributing

Contributions are welcome.

```bash
git clone https://github.com/shafin027/xv6-riscv-skill.git
cd xv6-riscv-skill
git checkout -b improve-skill
```

Then commit and open a pull request.

---

## License

MIT License. You can use, modify, and distribute this skill freely.

---

<p align="center">
  Made for OS students, xv6 hackers, and RISC-V learners.
</p>
