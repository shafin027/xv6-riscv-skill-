# xv6-riscv-expert

<p align="center">
  <a href="https://github.com/shafin027/xv6-riscv-skill-/releases">
    <img src="https://img.shields.io/github/release/shafin027/xv6-riscv-skill-?style=flat-square&color=blue" alt="GitHub Release">
  </a>
  <img src="https://img.shields.io/badge/xv6--riscv--expert-important?style=flat-square&color=orange" alt="xv6-riscv-expert">
  <img src="https://img.shields.io/badge/Claude~Code--skill-purple?style=flat-square" alt="Claude Code Skill">
  <a href="https://github.com/shafin027/xv6-riscv-skill-/blob/main/LICENSE">
    <img src="https://img.shields.io/github/license/shafin027/xv6-riscv-skill-?style=flat-square&color=green" alt="License">
  </a>
</p>

<p align="center">
  <a href="https://www.npmjs.com/package/skills-cli">
    <img src="https://img.shields.io/npm/v/skills-cli?style=flat-square&logo=npm&label=CLI" alt="npm">
  </a>
  <a href="https://www.npmjs.com/package/skills-cli">
    <img src="https://img.shields.io/npm/dm/skills-cli?style=flat-square&logo=npm&label=downloads" alt="npm downloads">
  </a>
  <a href="https://github.com/shafin027/xv6-riscv-skill-/stargazers">
    <img src="https://img.shields.io/github/stars/shafin027/xv6-riscv-skill-?style=flat-square&logo=github" alt="GitHub stars">
  </a>
  <a href="https://paypal.me/yourusername">
    <img src="https://img.shields.io/badge/PayPal-Support%20Development-00457C?style=flat-square&logo=paypal&logoColor=white" alt="PayPal">
  </a>
</p>

Expert assistant for MIT-style **xv6-riscv** & **SNU OS** assignments on 64-bit RISC-V.

<p align="center">
  <a href="https://skills.sh">
    <img src="screenshots/website.png" alt="xv6-riscv-expert" width="800">
  </a>
</p>

<p align="center">
  <b>If you find this useful, consider supporting the project:</b><br><br>
  <a href="https://paypal.me/yourusername">
    <img src="https://img.shields.io/badge/PayPal-Donate-00457C?style=for-the-badge&logo=paypal&logoColor=white" alt="PayPal Donate">
  </a>
</p>

<p align="center">
  <i>Other projects</i><br>
  <a href="https://github.com/shafin027">shafin027 GitHub</a>
</p>

---

## What's New in v1.0

### Complete xv6-riscv Assignment Support

```
+-----------------------------------------------------------------------------------------+
|  TARGET: xv6-riscv Assignment - RECOMMENDED SOLUTION SYSTEM                      |
+-----------------------------------------------------------------------------------------+
|                                                                                         |
|  SUPPORTED: System Calls, Scheduler, Virtual Memory, Traps, Process Management    |
|     Assignment Types: Lottery Scheduler, Copy-on-Write, USYSCALL, Tracing          |
|     Complete Workflow: 7-step syscall checklist, patch generation, testing            |
|                                                                                         |
|  KNOWLEDGE BASE:                                                                     |
|     • Complete xv6 file map (kernel/proc.h, vm.c, trap.c, etc.)               |
|     • System call workflow (7-step checklist)                                      |
|     • Scheduler patterns (lottery, priority, round-robin)                         |
|     • Virtual memory guide (Sv39 page tables, PTE flags)                          |
|     • Trap/interrupt debugging (scause, sepc, stval)                             |
|     • File system patterns (inodes, logging, buffer cache)                          |
|     • GDB debugging commands (breakpoints, register inspection)                        |
|     • Answer templates (implementation, debugging, exam prep)                        |
|     • Common assignment patterns (USYSCALL, COW fork, tracing)                       |
|                                                                                         |
|  KEY FEATURES:                                                                      |
|     • Automatic RISC-V register analysis (scause, sepc, stval, a0-a7)              |
|     • Minimal xv6-style C patches with explanations                              |
|     • Test commands included (make qemu, make qemu-gdb)                            |
|     • Common mistakes highlighted for each assignment type                        |
|     • Exam-friendly explanations with code examples                              |
|                                                                                         |
|  AVOID (Anti-Patterns):                                                              |
|     • Generic Linux answers (this is xv6-riscv specific)                            |
|     • Using libc in kernel code (use xv6 functions)                              |
|     • Confusing user/kernel printf (different implementations)                      |
|     • Forgetting to hold p->lock when modifying process fields                    |
|     • Mixing up user virtual and physical addresses                             |
|                                                                                         |
|  PRE-DELIVERY CHECKLIST:                                                            |
|     [ ] xv6-style C (lowercase names, small functions)                           |
|     [ ] All 7 syscall files checked (syscall.h, syscall.c, sysproc.c, etc.)        |
|     [ ] PTE flags correct (PTE_V, PTE_R, PTE_W, PTE_X, PTE_U)                    |
|     [ ] GDB commands included for debugging                                        |
|     [ ] Patch file creation instructions (git diff --staged > ID.patch)              |
|                                                                                         |
+-----------------------------------------------------------------------------------------+
```

### How the Expert System Works

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│  1. USER REQUEST                                                │
│     "Implement a lottery scheduler for xv6-riscv"                    │
└─────────────────────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────────────────────┐
│  2. MULTI-DOMAIN SEARCH (5 parallel searches)                   │
│     • Assignment type (lottery scheduler)                             │
│     • File locations (proc.h, proc.c, sysproc.c)                       │
│     • Random number generation (do_rand algorithm)                      │
│     • Test program structure (test_scheduler.c)                         │
│     • GDB debugging (breakpoints, register inspection)                    │
└─────────────────────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────────────────────┐
│  3. EXPERT REASONING ENGINE                                       │
│     • Match assignment → xv6 subsystem rules                         │
│     • Apply scheduler priorities (BM25 ranking)                          │
│     • Filter anti-patterns (no Linux answers)                          │
│     • Process decision rules (JSON conditions)                           │
└─────────────────────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────────────────────┐
│  4. COMPLETE ASSIGNMENT SOLUTION                               │
│     Files to change + Patch / code + Why it works                      │
│     Test commands + Common mistakes                                   │
│     + Exam-friendly explanation                                       │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

## Features

- **Complete xv6 File Map** - All kernel files documented (proc.h, vm.c, trap.c, etc.)
- **7-Step System Call Workflow** - Never miss a file again
- **Scheduler Patterns** - Lottery, priority, round-robin implementations
- **Virtual Memory Guide** - Sv39 page tables, PTE flags, walk(), copyin/copyout
- **Trap & Interrupt Debugging** - scause, sepc, stval register analysis
- **File System Patterns** - Inodes, logging, buffer cache operations
- **GDB Debugging Commands** - Breakpoints, register inspection, backtraces
- **Answer Templates** - Implementation, debugging, and exam prep structures
- **161 Reasoning Rules** - Assignment-specific expert knowledge base

---

## Quick Install

### Option 1: Using Skills CLI (Recommended)

```bash
npx skills add shafin027/xv6-riscv-skill-
```

### Option 2: Manual Install

```bash
git clone https://github.com/shafin027/xv6-riscv-skill-.git ~/.claude/skills/xv6-riscv-expert
```

### Option 3: Local Project Install

```bash
cd /path/to/your/project
npx skills add shafin027/xv6-riscv-skill- --local
```

---

## Usage

### Slash Command

```bash
/xv6-riscv-expert
```

### Automatic Triggering

Claude Code will use the skill when you ask questions like:

```
I need to add a new system call to xv6-riscv.
```

```
How do I implement a lottery scheduler in xv6?
```

```
Debug this xv6 page fault: scause=15, stval=0x0.
```

---

## Supported Assignment Types

| Type | Examples | Status |
|------|----------|--------|
| **System Calls** | `settickets`, `getpid`, tracing, custom syscalls | ✅ |
| **Scheduler** | Lottery scheduler, priority scheduler, round-robin | ✅ |
| **Virtual Memory** | Page tables, PTEs, `vmprint`, COW, USYSCALL | ✅ |
| **Traps & Interrupts** | `usertrap`, page faults, timer interrupts | ✅ |
| **Process Management** | `fork`, `exit`, `wait`, process states | ✅ |
| **Locks & Concurrency** | Spinlocks, sleeplocks, race conditions | ✅ |
| **File System** | Inodes, logging, buffer cache, large files | ✅ |
| **Boot & Init** | Kernel prints, init process, QEMU setup | ✅ |

---

## Example Workflows

### Example 1: Adding a New System Call

**Prompt:**
```
I need to add a system call called settickets(int n) to xv6-riscv
```

**Skill Response:**
- ✅ Lists all files to change (syscall.h, syscall.c, sysproc.c, user.h, usys.pl)
- ✅ Provides exact code patches
- ✅ Explains why each change works
- ✅ Gives test commands (`make qemu`)
- ✅ Shows common mistakes to avoid

### Example 2: Lottery Scheduler Assignment

**Prompt:**
```
Implement a lottery scheduler for xv6-riscv where each process 
has tickets and the scheduler picks a random winner
```

**Skill Response:**
- ✅ Step-by-step implementation plan
- ✅ Complete code for `proc.h`, `proc.c`, `sysproc.c`
- ✅ Random number generator implementation
- ✅ Test program (`test_scheduler.c`)
- ✅ Patch file creation instructions

### Example 3: Debugging a Page Fault

**Prompt:**
```
My xv6 kernel panics with scause=15 (store page fault). 
The fault happens in sys_write. Here's my code...
```

**Skill Response:**
- ✅ Identifies likely cause (PTE permissions, user pointer)
- ✅ Shows what to inspect (`copyout`, `walk()`, PTE flags)
- ✅ Provides exact fix
- ✅ Gives validation steps

---

## Star History

<p align="center">
  <a href="https://star-history.com/#shafin027/xv6-riscv-skill-&type=Date">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg/shafin027/xv6-riscv-skill-?type=Date&theme=dark" />
      <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg/shafin027/xv6-riscv-skill-?type=Date" />
      <img alt="Star History Chart" src="https://api.star-history.com/svg/shafin027/xv6-riscv-skill-?type=Date" />
    </picture>
  </a>
</p>

---

## xv6-riscv Setup

Before using this skill, ensure you have xv6-riscv set up:

### 1. Install Prerequisites

```bash
# Ubuntu/Debian
sudo apt update
sudo apt install git build-essential gdb-multiarch qemu-system-misc \
                 gcc-riscv64-linux-gnu binutils-riscv64-linux-gnu
```

### 2. Clone xv6-riscv

```bash
git clone https://github.com/mit-pdos/xv6-riscv.git
cd xv6-riscv
```

### 3. Build and Run

```bash
make clean
make qemu
```

---

## Resources

- [xv6-riscv Official Repository](https://github.com/mit-pdos/xv6-riscv)
- [xv6 Book (MIT)](https://pdos.csail.mit.edu/6.828/2020/xv6-book.html)
- [RISC-V Documentation](https://riscv.org/technical/specifications/)
- [SNU xv6-riscv-snu](https://github.com/snu-csl/xv6-riscv-snu)

---

## Contributing

Found a bug or want to improve the skill? Contributions welcome!

1. Fork the repo
2. Create your feature branch (`git checkout -b feature/amazing-improvement`)
3. Commit your changes (`git commit -m 'Add some amazing improvement'`)
4. Push to the branch (`git push origin feature/amazing-improvement`)
5. Open a Pull Request

---

## License

**MIT License** — feel free to use, modify, and distribute.

---

<p align="center">
  <b>Made with ❤️ for OS students, xv6 hackers, and RISC-V enthusiasts</b>
</p>

<p align="center">
  <sub>Part of the <a href="https://skills.sh/">Claude Code Skills</a> ecosystem</sub>
</p>
