# 🐧 Experiment 2 — Basic Linux Commands, Run Levels & Help Utilities

> **Course:** Introduction to Linux with Bash Scripting Lab  
> **Instructor:** Dr. Rajesh Kumar  
> **System:** KDE Neon User Edition (GNU/Linux 6.17.0-14-generic x86_64) — VMware Virtual Platform  
> **CO Mapped:** CO1 — Familiarity with Linux environment, command-line interface, and system utilities

---

## 🎯 Learning Outcomes

After completing this experiment, you will be able to:

- **LO1:** Execute basic Linux system and user-level commands
- **LO2:** Understand Linux run levels (systemd targets)
- **LO3:** Use Linux help utilities to learn command syntax and options
- **LO4:** Improve efficiency using command auto-completion

---

## 📖 Theory

### Linux Command Line Interface (CLI)
The Linux CLI allows users to interact with the OS by typing commands. It provides precise control over system operations and is faster and more powerful than graphical interfaces for many tasks.

### System Run Levels / Targets
Modern Linux distributions use **systemd targets** instead of traditional run levels to define the system's operating state.

| Target | Description |
|---|---|
| `graphical.target` | Multi-user mode with GUI |
| `multi-user.target` | Multi-user mode without GUI |
| `rescue.target` | Single-user rescue/recovery mode |
| `poweroff.target` | Shutdown the system |
| `reboot.target` | Reboot the system |

### Linux Help Utilities

| Utility | Purpose |
|---|---|
| `man <command>` | Displays the full manual page for a command |
| `<command> --help` | Shows brief usage and options |
| `Tab` key | Auto-completes commands and file names |

---

## 🗂️ Commands Reference

| Command | Description |
|---|---|
| `pwd` | Display current working directory |
| `ls` | List files and directories |
| `cd` | Change directory |
| `whoami` | Display current logged-in user |
| `date` | Show system date and time |
| `uptime` | Show how long the system has been running |
| `man` | Display manual pages |
| `--help` | Display command help |
| `systemctl` | Manage system services and targets |
| `runlevel` | Display previous and current run level |
| `clear` | Clear the terminal screen |

---

## 🚀 Procedure & Output

### Step 1 — Log in & Open Terminal
Log in to the Linux virtual machine (KDE Neon on VMware) and open the Terminal.

### Step 2 — Execute Basic System Commands

```bash
pwd
```
**Output:**
```
/home/skde
```

```bash
ls
```
**Output:**
```
arithmeti.sh.save  Documents    file_list.txt   inode_test.txt  linux_lab      params.sh  Public              simple.sh
Desktop            Downloads    file_ops         interactive.sh  Music          Pictures   Sankarshan_2301410027  Templates
                                                                                           thinclient_drives      Videos
```

```bash
whoami
```
**Output:**
```
skde
```

```bash
date
```
**Output:**
```
Thursday 30 April 2026 06:37:50 PM IST
```

```bash
uptime
```
**Output:**
```
18:37:55 up 8 min,  1 user,  load average: 0.31, 0.26, 0.16
```

---

### Step 3 — Navigate Directories

```bash
cd /home        # Navigate to /home directory
cd ~            # Return to home directory
```

---

### Step 4 — Use Manual Pages

```bash
man ls
```
> Opens the full manual for the `ls` command. Press `q` to exit.

---

### Step 5 — Use Help Options

```bash
ls --help
```
**Output (excerpt):**
```
Usage: ls [OPTION]... [FILE]...
List information about the FILEs (the current directory by default).
Sort entries alphabetically if none of -cftuvSUX nor --sort is specified.

  -a, --all                  do not ignore entries starting with .
  -A, --almost-all           do not list entries implied . and ..
      --author               with -l, print the author of each file
  -b, --escape               print C-style escapes for nongraphic characters
      --block-size=SIZE      with -l, scale sizes by SIZE when printing them;
```

---

### Step 6 — Switch to Multi-User Target (`sudo init 3`)

```bash
sudo init 3
```
**Output:**  
System switches to **TTY text mode** (no GUI). Login prompt appears:
```
KDE neon User Edition skde-vmwarevirtualplatform tty1
skde-vmwarevirtualplatform login: skde
Password:
Welcome to KDE neon User Edition (GNU/Linux 6.17.0-14-generic x86_64)
...
skde@skde-vmwarevirtualplatform:~$
```

---

### Step 7 — Switch Back to Graphical Target (`sudo init 5`)

```bash
sudo init 5
```
**Output:**  
System returns to the **KDE graphical desktop environment**.

---

### Step 8 — Check Run Level & Default Target

```bash
runlevel
```
**Output:**
```
3 5
```
*(Previous run level: 3 | Current run level: 5)*

```bash
systemctl get-default
```
**Output:**
```
graphical.target
```

> ⚠️ **Note:** Attempting `systemctl isolate multi-user.target` and `systemctl isolate graphical.target` without elevated privileges returns:
> ```
> Failed to start multi-user.target: Access denied
> Failed to start graphical.target: Access denied
> ```
> Use `sudo init 3` / `sudo init 5` instead, as shown above.

---

### Step 9 — Clear the Terminal

```bash
clear
```

---

## ✅ Expected Output

- Successful execution of all basic Linux commands
- Manual pages and help documentation displayed correctly
- Current system run level identified as `3 5` and default target as `graphical.target`
- Run level switching demonstrated using `sudo init 3` and `sudo init 5`

---

## 📸 Screenshots

| # | Description |
|---|---|
| 1 | Output of `pwd`, `ls`, `whoami`, `date`, `uptime`, `cd`, `man ls`, `ls --help` |
| 2 | TTY login screen after `sudo init 3` (multi-user text mode) |
| 3 | Output of `runlevel`, `systemctl get-default`, and access denied errors for `systemctl isolate` |

---

## ⚠️ Guidelines

- Always refer to `man` pages before using unfamiliar commands
- Use `sudo init 3` / `sudo init 5` for run level switching if `systemctl isolate` is restricted
- Use Tab auto-completion to reduce typing errors
- Document all command outputs with screenshots
- Practice commands multiple times to build confidence

---

## 📝 Result

Basic Linux system commands, run levels, and help utilities were successfully explored and executed. Run level switching was demonstrated using `sudo init 3` (multi-user/text mode) and `sudo init 5` (graphical mode). The student gained practical understanding of Linux command-line interaction and documentation mechanisms.
