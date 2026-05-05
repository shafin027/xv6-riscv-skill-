# xv6-riscv-expert

<p align="center">
  <a href="https://skills.sh/shafin027/xv6-riscv-skill-">
    <img src="https://img.shields.io/badge/Install%20Skill-Click%20Here-purple?style=for-the-badge" alt="Install Skill">
  </a>
</p>

<p align="center">
  <a href="https://github.com/shafin027/xv6-riscv-skill-/stargazers">
    <img src="https://img.shields.io/github/stars/shafin027/xv6-riscv-skill-?style=social" alt="GitHub stars">
  </a>
  <a href="https://github.com/shafin027/xv6-riscv-skill-/network/members">
    <img src="https://img.shields.io/github/forks/shafin027/xv6-riscv-skill-?style=social" alt="GitHub forks">
  </a>
  <a href="https://github.com/shafin027/xv6-riscv-skill-/watchers">
    <img src="https://img.shields.io/github/watchers/shafin027/xv6-riscv-skill-?style=social" alt="Watchers">
  </a>
  <a href="https://github.com/shafin027/xv6-riscv-skill-/issues">
    <img src="https://img.shields.io/github/issues/shafin027/xv6-riscv-skill-?style=social" alt="Issues">
  </a>
  <a href="LICENSE">
    <img src="https://img.shields.io/github/license/shafin027/xv6-riscv-skill-?style=social" alt="License">
  </a>
</p>

---

## 📖 What Is This?

`xv6-riscv-expert` is a **Claude Code Skill** designed for students and developers working with MIT-style `xv6-riscv` and SNU's `xv6-riscv-snu` operating system assignments.

### ✨ Perfect For:

| Use Case | Description |
|----------|-------------|
| 🎓 **Coursework** | CSE321 / OS assignments (xv6-riscv) |
| 🔧 **Kernel Dev** | System calls, scheduler, virtual memory |
| 🐛 **Debugging** | Traps, page faults, locks |
| 📚 **Learning** | OS concepts, RISC-V architecture |

---

## 🚀 Quick Install

### Option 1: One-Line Install (Recommended)

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

## 🎯 Usage

### Slash Command

```bash
/xv6-riscv-expert
```

### Automatic Triggering

Claude Code will use the skill when you ask questions like:

```
I need to add a new syscall to xv6-riscv.
```

```
How do I implement a lottery scheduler in xv6?
```

```
Debug this xv6 page fault: scause=15, stval=0x0.
```

---

## 🛠️ Supported Assignment Types

| Type | Examples | Status |
|------|----------|--------|
| **System Calls** | `settickets`, `getpid`, tracing, custom syscalls | ✅ |
| **Scheduler** | Lottery scheduler, priority scheduler, round-robin | ✅ |
| **Virtual Memory** | Page tables, PTEs, `vmprint`, COW, USYSCALL | ✅ |
| **Traps & Interrupts** | `usertrap`, page faults, timer interrupts | ✅ |
| **Process Management** | `fork`, `exit`, `wait`, process states | ✅ |
| **Locks & Concurrency** | Spinlocks, sleeplocks, race conditions | ✅ |
| **File System** | Inodes, logging, buffer cache | ✅ |

---

## 📚 Skill Knowledge Base

### Core Files Map

| File | Purpose |
|------|---------|
| `kernel/proc.h` | `struct proc`, process states, fields |
| `kernel/proc.c` | Process lifecycle, scheduler, `fork`, `exit` |
| `kernel/syscall.c` | Syscall dispatcher and table |
| `kernel/syscall.h` | Syscall numbers |
| `kernel/trap.c` | Trap handling, interrupts, exceptions |
| `kernel/vm.c` | Page tables, virtual memory, mapping |
| `kernel/riscv.h` | RISC-V registers, PTE flags |
| `user/user.h` | User-space function declarations |

### 🎯 Answer Templates

**Implementation Answer:**
1. Files to change
2. Patch / code
3. Why this works
4. How to test
5. Common mistakes

**Debugging Answer:**
1. Likely cause
2. What to inspect
3. Exact command(s)
4. Fix
5. Validation

---

## 🎯 Example Workflows

### Example 1: Adding a New Syscall

**Prompt:**
```
I need to add a syscall called settickets(int n) to xv6-riscv
```

**Skill Response:**
- ✅ Lists all files to change
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

## 🔧 xv6-riscv Setup

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

### 4. Debug with GDB

Terminal 1:
```bash
make qemu-gdb
```

Terminal 2:
```bash
riscv64-linux-gnu-gdb kernel/kernel
```

---

## 📋 Assignment Checklist

When working on xv6 assignments, the skill will help you:

- [ ] Identify assignment type
- [ ] List all files to modify
- [ ] Provide minimal correct patches
- [ ] Explain why the solution works
- [ ] Include test commands
- [ ] Warn about common mistakes
- [ ] Help create patch files (`git diff --staged > ID.patch`)

---

## 🤝 Contributing

Found a bug or want to improve the skill? Contributions welcome!

1. Fork the repo
2. Create your feature branch (`git checkout -b feature/amazing-improvement`)
3. Commit your changes (`git commit -m 'Add some amazing improvement'`)
4. Push to the branch (`git push origin feature/amazing-improvement`)
5. Open a Pull Request

---

## Star History

<a href="https://www.star-history.com/?repos=shafin027%2Fxv6-riscv-skill&type=date&legend=top-left">
 <picture>
   <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/chart?repos=shafin027/xv6-riscv-skill&type=date&theme=dark&legend=top-left" />
   <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/chart?repos=shafin027/xv6-riscv-skill&type=date&legend=top-left" />
   <img alt="Star History Chart" src="https://api.star-history.com/chart?repos=shafin027/xv6-riscv-skill&type=date&legend=top-left" />
 </picture>
</a>


## 📄 License

**MIT License** — feel free to use, modify, and distribute.

---

## 🔗 Resources

- [xv6-riscv Official Repository](https://github.com/mit-pdos/xv6-riscv)
- [xv6 Book (MIT)](https://pdos.csail.mit.edu/6.828/2020/xv6-book.html)
- [RISC-V Documentation](https://riscv.org/technical/specifications/)
- [SNU xv6-riscv-snu](https://github.com/snu-csl/xv6-riscv-snu)

---

## 💬 Support

Having issues?

1. Open an issue on [GitHub](https://github.com/shafin027/xv6-riscv-skill-/issues)
2. Ask in the [Claude Code Discord](https://discord.gg/claude-code)

---

<p align="center">
  <b>Made with ❤️ for OS students, xv6 hackers, and RISC-V enthusiasts</b>
</p>

<p align="center">
  <sub>Part of the <a href="https://skills.sh/">Claude Code Skills</a> ecosystem</sub>
</p>
