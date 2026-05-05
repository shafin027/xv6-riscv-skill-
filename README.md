# xv6-riscv-expert

> Claude Code Skill — Expert assistant for MIT-style xv6 on 64-bit RISC-V operating system assignments.

[![Install Skill](https://img.shields.io/badge/Install%20Skill-Click%20Here-purple?style=for-the-badge)](https://skills.sh/shafin027/xv6-riscv-skill)

## 📊 GitHub Stats

[![Stars](https://img.shields.io/github/stars/shafin027/xv6-riscv-skill?style=social)](https://github.com/shafin027/xv6-riscv-skill/stargazers)
[![Forks](https://img.shields.io/github/forks/shafin027/xv6-riscv-skill?style=social)](https://github.com/shafin027/xv6-riscv-skill/network/members)
[![Watchers](https://img.shields.io/github/watchers/shafin027/xv6-riscv-skill?style=social)](https://github.com/shafin027/xv6-riscv-skill/watchers)
[![Issues](https://img.shields.io/github/issues/shafin027/xv6-riscv-skill)](https://github.com/shafin027/xv6-riscv-skill/issues)
[![License](https://img.shields.io/github/license/shafin027/xv6-riscv-skill)](LICENSE)
[![GitHub release](https://img.shields.io/github/release/shafin027/xv6-riscv-skill)](https://github.com/shafin027/xv6-riscv-skill/releases)

### 🔥 Live Stats

![GitHub Stats](https://github-readme-stats.vercel.app/api?username=shafin027&repo=xv6-riscv-skill&show_icons=true&theme=radical)
![GitHub Stars](https://github-readme-stats.vercel.app/api?username=shafin027&repo=xv6-riscv-skill&show_icons=true&count_private=true&theme=radical#gh-light-mode-only)
![GitHub Forks](https://img.shields.io/github/forks/shafin027/xv6-riscv-skill?label=Forks&style=for-the-badge&color=blueviolet)
![GitHub Stars](https://img.shields.io/github/stars/shafin027/xv6-riscv-skill?label=Stars&style=for-the-badge&color=yellow)

## 📖 Description

This skill transforms Claude Code into an **xv6-riscv expert** — specifically designed to help students and developers solve, implement, debug, and explain **xv6-riscv** and **SNU xv6-riscv-snu** operating system assignments.

Perfect for:
- 🎓 **CSE321 / OS coursework** (xv6-riscv assignments)
- 🔧 **Kernel development** (syscalls, scheduler, virtual memory)
- 🐛 **Debugging xv6** (traps, page faults, locks)
- 📚 **OS concept learning** (process management, file systems)

---

## 🚀 Quick Install

### Option 1: One-line install (Recommended)

```bash
npx skills add shafin027/xv6-riscv-skill
```

### Option 2: Manual install

```bash
git clone https://github.com/shafin027/xv6-riscv-skill.git ~/.claude/skills/xv6-riscv-expert
```

### Option 3: Install to current project

```bash
cd /path/to/your/project
npx skills add shafin027/xv6-riscv-skill --local
```

---

## 🛠️ Supported Assignment Types

| Assignment Type | Examples |
|----------------|----------|
| **System Calls** | Adding new syscalls, `settickets`, `getpid`, tracing |
| **Scheduler** | Lottery scheduler, priority scheduler, round-robin |
| **Virtual Memory** | Page tables, PTEs, `vmprint`, USYSCALL, copy-on-write |
| **Traps & Interrupts** | `usertrap`, `kerneltrap`, page faults, timer interrupts |
| **Process Management** | `fork`, `exit`, `wait`, process states |
| **Locks & Concurrency** | Spinlocks, sleeplocks, race conditions, deadlocks |
| **File System** | Inodes, logging, buffer cache, large files |
| **Boot & Init** | Kernel prints, init process, QEMU setup |

---

## 📘 Usage

### Method 1: Slash command

```bash
/xv6-riscv-expert
```

### Method 2: Automatic triggering

Just mention xv6-related keywords in your prompt:

```
I need to add a new syscall to xv6-riscv
```

```
How do I implement a lottery scheduler in xv6?
```

```
Debug this page fault in my xv6 kernel
```

### Method 3: Explicit invocation

```bash
claude -p "Use xv6-riscv-expert to help me debug this trap"
```

---

## 🎯 Example Workflows

### Example 1: Adding a new syscall

**Prompt:**
```
I need to add a syscall called settickets(int n) to xv6-riscv
```

**Skill response:**
1. Lists all files to change
2. Provides exact code patches
3. Explains why each change works
4. Gives test commands (`make qemu`)
5. Shows common mistakes to avoid

### Example 2: Debugging a page fault

**Prompt:**
```
My xv6 kernel panics with scause=15 (store page fault). 
The fault happens in sys_write. Here's my code...
```

**Skill response:**
1. Identifies likely cause (PTE permissions, user pointer)
2. Shows what to inspect (`copyout`, `walk()`, PTE flags)
3. Provides exact fix
4. Gives validation steps

### Example 3: Lottery scheduler assignment

**Prompt:**
```
Implement a lottery scheduler for xv6-riscv where each process 
has tickets and the scheduler picks a random winner
```

**Skill response:**
1. Step-by-step implementation plan
2. Complete code for `proc.h`, `proc.c`, `sysproc.c`
3. Random number generator implementation
4. Test program (`test_scheduler.c`)
5. Patch file creation instructions

---

## 📚 Skill Knowledge Base

The skill includes:

- ✅ **Complete xv6 file map** (`kernel/proc.h`, `vm.c`, `trap.c`, etc.)
- ✅ **System call workflow** (7-step checklist)
- ✅ **Scheduler patterns** (lottery, priority, round-robin)
- ✅ **Virtual memory guide** (Sv39 page tables, PTE flags)
- ✅ **Trap/interrupt debugging** (scause, sepc, stval)
- ✅ **File system patterns** (inodes, logging, buffer cache)
- ✅ **GDB debugging commands** (breakpoints, register inspection)
- ✅ **Answer templates** (implementation, debugging, exam prep)
- ✅ **Common assignment patterns** (USYSCALL, COW fork, tracing)

---

## 🔧 xv6-riscv Setup

Before using this skill, ensure you have xv6-riscv set up:

### 1. Install prerequisites

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

### 3. Build and run

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

## 📄 License

MIT License — feel free to use, modify, and distribute.

---

## 🔗 Resources

- [xv6-riscv Official Repository](https://github.com/mit-pdos/xv6-riscv)
- [xv6 Book (MIT)](https://pdos.csail.mit.edu/6.828/2020/xv6-book.html)
- [RISC-V Documentation](https://riscv.org/technical/specifications/)
- [SNU xv6-riscv-snu](https://github.com/snu-csl/xv6-riscv-snu)

---

## 💬 Support

Having issues?

1. Check the [troubleshooting section](https://skills.sh/shafin027/xv6-riscv-skill/docs/troubleshooting)
2. Open an issue on [GitHub](https://github.com/shafin027/xv6-riscv-skill/issues)
3. Ask in the [Claude Code Discord](https://discord.gg/claude-code)

---

**Made with ❤️ for OS students and RISC-V enthusiasts**
