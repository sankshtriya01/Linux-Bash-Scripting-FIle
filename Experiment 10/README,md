# 🐚 Experiment 10: Linux Shells & Bash Shell Scripting Lab

In Linux, the shell acts as an interface between the user and the operating system kernel. Different types of shells provide varied features, scripting capabilities, and command-line behaviors. Among these, **Bash (Bourne Again Shell)** is the most widely used shell due to its scripting power and ease of use. This experiment covers identifying shell types, switching between them, and writing a simple Bash script using variables.

---

## 🖥️ Environment

| Property | Value |
|----------|-------|
| **Platform** | VMware Virtual Platform |
| **Shell** | Bash (`/bin/bash`) |
| **User** | `skde` |
| **Script File** | `simple.sh` |

---

## 🎯 Course Outcome Mapping

| Code | Outcome |
|------|---------|
| **CO1** | Familiarity with Linux environment and shell types |
| **CO3** | Execution of commands and manipulation of shell environment |

---

## 📚 Learning Outcomes

After completing this experiment, the student will be able to:

- **LO1** — Identify and differentiate between various Linux shells
- **LO2** — Switch between different shells
- **LO3** — Write and execute a basic Bash shell script
- **LO4** — Use variables within shell scripts

---

## 📖 Theory

### What is a Shell?

A shell is a **command-line interpreter** that processes user commands and communicates with the kernel. It allows users to execute commands, manage files, and write scripts for automation.

### Types of Shells

Common shells available in Linux:

| Shell | Full Name | Description |
|-------|-----------|-------------|
| `sh` | Bourne Shell | The original Unix shell |
| `bash` | Bourne Again Shell | Enhanced `sh`; default on most Linux systems |
| `ksh` | Korn Shell | Combines features of `sh` and `csh` |
| `csh` | C Shell | C-like syntax scripting shell |
| `zsh` | Z Shell | Extended `bash` with extra features |

### Bash Shell

Bash is an enhanced version of `sh` that supports:
- Command history
- Job control
- Scripting with variables and control structures

### Shell Scripts

A shell script is a file containing a **sequence of commands** executed by the shell. It typically starts with a **shebang** line that specifies the interpreter:

```bash
#!/bin/bash
```

---

## 🧪 Commands & Observations

### Part A — Identifying Available Shells

#### 1. List All Valid Login Shells

```bash
cat /etc/shells
```

**Output:**
```
# /etc/shells: valid login shells
/bin/sh
/bin/bash
/usr/bin/bash
/bin/rbash
/usr/bin/rbash
/usr/bin/dash
```

> The `/etc/shells` file lists all valid login shells available on the system. Six shells are available on this machine.

---

#### 2. Check the Current Shell

```bash
echo $SHELL
```

**Output:**
```
/bin/bash
```

> `$SHELL` is an environment variable that holds the path to the current user's default shell. The active shell is confirmed as **Bash**.

---

### Part B — Switching Between Shells

#### 3. Switch to Bourne Shell (`sh`)

```bash
sh
```

**Output:**
```
$
```

> The prompt changes from `skde@skde-vmwarevirtualplatform:~$` to a plain `$`, indicating a successful switch to the Bourne shell (`sh`).

---

#### 4. Return to Bash

```bash
exit
```

> Typing `exit` inside `sh` terminates the child shell session and returns control back to the parent Bash shell.

---

### Part C — Writing a Simple Bash Script

#### 5. Create the Script File

```bash
nano simple.sh
```

> Opens the `nano` text editor to create a new script file named `simple.sh`.

**Script contents written inside `nano`:**

```bash
#!/bin/bash
echo "Welcome to Linux Shell Scripting"
name="Student"
echo "Hello $name"
```

| Line | Explanation |
|------|-------------|
| `#!/bin/bash` | Shebang — tells the OS to use Bash as the interpreter |
| `echo "Welcome..."` | Prints a welcome message |
| `name="Student"` | Declares a variable `name` with value `Student` |
| `echo "Hello $name"` | Prints the variable value using `$` prefix |

---

### Part D — Executing the Script

#### 6. Grant Execute Permission

```bash
chmod +x simple.sh
```

> Makes `simple.sh` executable. Without this step, the script cannot be run directly.

---

#### 7. Run the Script

```bash
./simple.sh
```

**Output:**
```
Welcome to Linux Shell Scripting
Hello Student
```

> The `./` prefix tells the shell to run the script from the current directory. The variable `$name` is correctly substituted with `Student`.

---

## 📋 Command Summary

| Command | Description |
|---------|-------------|
| `cat /etc/shells` | List all valid login shells on the system |
| `echo $SHELL` | Display the current active shell |
| `sh` | Switch to Bourne shell |
| `exit` | Exit current shell and return to parent shell |
| `nano simple.sh` | Create/edit a shell script |
| `chmod +x simple.sh` | Grant execute permission to the script |
| `./simple.sh` | Execute the shell script |

---

## ✅ Expected Output

- List of all available shells displayed via `/etc/shells`
- Current shell identified as `/bin/bash`
- Successfully switched to `sh` and returned to `bash` using `exit`
- Bash script executed correctly with variable substitution output:

```
Welcome to Linux Shell Scripting
Hello Student
```

---

## 📄 Script File Reference

**`simple.sh`**

```bash
#!/bin/bash
echo "Welcome to Linux Shell Scripting"
name="Student"
echo "Hello $name"
```

---

## 📌 Result

Different types of Linux shells were identified using `/etc/shells`, the active shell was verified using `$SHELL`, shell switching was demonstrated using `sh` and `exit`, and a simple Bash shell script using variables was successfully written and executed.

---

## ⚠️ Guidelines & Best Practices

- Always include the **shebang line** (`#!/bin/bash`) at the top of every script
- Grant **execute permission** with `chmod +x` before running a script
- Use **meaningful variable names** for readable and maintainable scripts
- Verify the current shell with `echo $SHELL` before writing scripts
- Use `exit` to safely return to the parent shell after switching

---

*Experiment conducted on VMware Virtual Platform | Linux Bash Shell*
