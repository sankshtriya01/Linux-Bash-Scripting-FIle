# 📂 Experiment 3: Linux File & Directory Management Lab

File and directory management is a fundamental operation in any operating system. In Linux, effective handling of files and directories is essential for system administration, software development, and cybersecurity tasks. Unlike graphical file managers, Linux primarily relies on command-line utilities to create, view, modify, and manage files with precise control over permissions and access rights.

---

## 🖥️ Environment

| Property | Value |
|----------|-------|
| **Platform** | VMware Virtual Platform |
| **Shell** | Bash |
| **User** | `skde` |
| **Home Directory** | `/home/skde` |
| **Working Directory** | `~/linux_lab` |

---

## 🎯 Course Outcome Mapping

| Code | Outcome |
|------|---------|
| **CO1** | Familiarity with Linux environment, command-line interface, and system utilities |

---

## 📚 Learning Outcomes

After completing this experiment, the student will be able to:

- **LO1** — Navigate the Linux file system using command-line tools
- **LO2** — Create, list, and organize files and directories
- **LO3** — Understand and interpret Linux file and directory permissions
- **LO4** — Create and edit text files using `nano` and `vi` editors

---

## 📖 Theory

### Linux File System

Linux follows a **hierarchical file system** structure starting from the root directory `/`. All files and directories are organized in a tree-like structure, enabling efficient file management and security control.

### Files and Directories

- **Files** — Store data such as text, scripts, or binaries
- **Directories** — Act as containers that organize files and other directories

### File and Directory Permissions

Linux enforces security using a permission model that defines access at three levels:

| Permission | Symbol | Meaning |
|------------|--------|---------|
| Read | `r` | View file contents or list directory contents |
| Write | `w` | Modify a file or directory |
| Execute | `x` | Execute a file or access a directory |

Permissions are assigned to three entities:

| Entity | Description |
|--------|-------------|
| **Owner** | The user who created the file |
| **Group** | Users sharing a common group |
| **Others** | All other users on the system |

### Text Editors

| Editor | Description |
|--------|-------------|
| `nano` | Beginner-friendly, menu-driven text editor |
| `vi` | Powerful modal editor commonly used in Unix/Linux systems |

---

## 🧪 Commands & Observations

### 1. Show Current Directory

```bash
pwd
```

**Output:**
```
/home/skde
```

> `pwd` (Print Working Directory) displays the full path of the current location in the file system.

---

### 2. List Files and Directories

```bash
ls
```

**Output:**
```
arithmetic.sh  arithmeti.sh.save  Desktop  Documents  Downloads  file_list.txt
file_ops  inode_test.txt  interactive.sh  Music  params.sh  Pictures
Public  simple.sh  Templates  thinclient_drives  Videos
```

> Lists all files and directories in the home directory without details.

---

### 3. Detailed Directory Listing (Error Encountered)

```bash
ls-l
```

**Output:**
```
ls-l: command not found
```

> Typed without a space. Linux interpreted `ls-l` as a single unknown command.

---

### 4. Correct Detailed Listing

```bash
ls -l
```

**Output (partial):**
```
total 64
-rw-rw-r-- 1 skde skde   50 Apr 21 12:10 arithmetic.sh
-rw------- 1 skde skde    2 Apr 21 12:07 arithmeti.sh.save
drwxr-xr-x 2 skde skde 4096 Feb 12 23:30 Desktop
drwxr-xr-x 2 skde skde 4096 Feb 12 23:30 Documents
drwxr-xr-x 2 skde skde 4096 Feb 12 23:30 Downloads
-rw-rw-r-- 1 skde skde  227 Apr 24 13:46 file_list.txt
drwxrwxr-x 3 skde skde 4096 Apr 24 09:30 file_ops
-rw-rw-r-- 1 skde skde    0 Apr 24 13:42 inode_test.txt
-rwxrwxr-x 1 skde skde   88 Apr 21 12:01 interactive.sh
drwxr-xr-x 2 skde skde 4096 Feb 12 23:30 Music
-rw-rw-r-- 1 skde skde   90 Apr 21 12:03 params.sh
drwxr-xr-x 2 skde skde 4096 Feb 12 23:30 Pictures
drwxr-xr-x 2 skde skde 4096 Feb 12 23:30 Public
-rwxrwxr-x 1 skde skde   87 Mar 27 13:36 simple.sh
drwxr-xr-x 2 skde skde 4096 Feb 12 23:30 Templates
drwxrwxr-t 2 skde skde 4096 Feb 12 23:46 thinclient_drives
drwxr-xr-x 2 skde skde 4096 Feb 12 23:30 Videos
```

> The `-l` flag displays detailed information: permissions, links, owner, group, size, date, and name.

**Reading a permission string — Example: `-rw-rw-r--`**

```
- rw- rw- r--
│  │   │   └── Others: read only
│  │   └────── Group:  read + write
│  └────────── Owner:  read + write
└───────────── File type: - (regular file), d (directory)
```

---

### 5. Create a New Directory & Navigate Into It

```bash
mkdir linux_lab
cd linux_lab
```

> `mkdir` creates the directory `linux_lab`. `cd` changes the working directory into it. The prompt updates to `~/linux_lab$`.

---

### 6. Create Empty Files

```bash
touch file1.txt file2.txt
```

> Creates two empty files simultaneously inside `linux_lab/`.

---

### 7. Edit a File Using `nano`

```bash
nano file1.txt
```

> Opens `file1.txt` in the `nano` editor.

**Inside nano:**
- Type the desired text (e.g., `Hello!`)
- Press `Ctrl+O` to save (write out)
- Press `Enter` to confirm the filename
- Press `Ctrl+X` to exit

---

### 8. Edit a File Using `vi`

```bash
vi file2.txt
```

> Opens `file2.txt` in the `vi` editor.

**Inside vi:**

| Key / Command | Action |
|---------------|--------|
| `i` | Enter insert mode to start typing |
| `Esc` | Exit insert mode |
| `:wq` | Save and quit |
| `:q!` | Quit without saving |

---

### 9. Display File Contents

```bash
cat file1.txt
```

**Output:**
```
Hello!
```

> Prints the content of `file1.txt` to the terminal. Confirms text was saved correctly via `nano`.

---

### 10. Check File Permissions

```bash
ls -l
```

**Output:**
```
total 4
-rw-rw-r-- 1 skde skde 7 Apr 24 14:03 file1.txt
-rw-rw-r-- 1 skde skde 0 Apr 24 14:01 file2.txt
```

> `file1.txt` has 7 bytes (the text "Hello!\n"). `file2.txt` is still empty (0 bytes). Both have default permissions `664` (`rw-rw-r--`).

---

### 11. Change File Permissions

```bash
chmod 755 file1.txt
```

> Changes permissions of `file1.txt` using octal notation:

| Entity | Octal | Permission | Symbol |
|--------|-------|------------|--------|
| Owner | 7 | read + write + execute | `rwx` |
| Group | 5 | read + execute | `r-x` |
| Others | 5 | read + execute | `r-x` |

---

### 12. Verify Updated Permissions

```bash
ls -l file1.txt
```

**Output:**
```
-rwxr-xr-x 1 skde skde 7 Apr 24 14:03 file1.txt
```

> The permission string changed from `-rw-rw-r--` (664) to `-rwxr-xr-x` (755), confirming `chmod` was applied successfully.

---

## 📋 Command Summary

| Command | Description |
|---------|-------------|
| `pwd` | Show current working directory |
| `ls` | List files and directories |
| `ls -l` | Detailed listing with permissions, size, date |
| `mkdir linux_lab` | Create a new directory |
| `cd linux_lab` | Navigate into a directory |
| `touch file1.txt file2.txt` | Create empty files |
| `nano file1.txt` | Edit file using nano editor |
| `vi file2.txt` | Edit file using vi editor |
| `cat file1.txt` | Display file contents |
| `chmod 755 file1.txt` | Change file permissions |
| `ls -l file1.txt` | Verify permissions of a specific file |

---

## ⚠️ Errors Encountered

```bash
ls-l
# ls-l: command not found
```

> Missing space between `ls` and `-l`. Linux treats `ls-l` as a single unknown command name. Always use `ls -l` with a space.

---

## ✅ Expected Output

- Current directory displayed as `/home/skde`
- Full home directory listing shown with file details
- `linux_lab/` directory created and navigated into
- `file1.txt` edited with `nano`, content verified via `cat` as `Hello!`
- `file2.txt` created with `vi`
- Permissions of `file1.txt` changed from `664` → `755` and verified

---

## 📁 Final Directory Structure

```
~/linux_lab/
├── file1.txt    # -rwxr-xr-x (chmod 755) — contains "Hello!"
└── file2.txt    # -rw-rw-r-- (default 664) — empty
```

---

## 🔐 chmod Octal Reference

| Octal | Binary | Permission |
|-------|--------|------------|
| 7 | 111 | rwx |
| 6 | 110 | rw- |
| 5 | 101 | r-x |
| 4 | 100 | r-- |
| 0 | 000 | --- |

---

## 📌 Result

Basic Linux file and directory management commands were successfully executed. Files were created, edited using `nano` and `vi`, and file permissions were modified using `chmod`. The student gained practical understanding of the Linux file system structure and permission model.

---

## ⚠️ Guidelines & Best Practices

- Always include a **space** between a command and its flags (`ls -l`, not `ls-l`)
- Use `nano` for quick edits; use `vi` for advanced or remote server editing
- Always verify permissions with `ls -l` after running `chmod`
- Use `chmod 755` for executable scripts and `chmod 644` for regular read-only files
- Never grant `777` (full access to all) unless absolutely necessary — it is a security risk

---

*Experiment conducted on VMware Virtual Platform | Linux Bash Shell*
