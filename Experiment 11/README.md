# 🗂️ Experiment 11: Inodes, I/O Redirection, Pipes & Process Control Lab

Linux internally manages files using data structures known as **inodes**, which store metadata about files rather than file names. In addition, Linux provides powerful mechanisms such as input/output redirection, pipes, and process control commands to efficiently manage command execution and system resources. These concepts are fundamental for automation, scripting, system monitoring, and cybersecurity operations.

---

## 🖥️ Environment

| Property | Value |
|----------|-------|
| **Platform** | VMware Virtual Platform |
| **Shell** | Bash |
| **User** | `skde` |
| **Test File** | `inode_test.txt`, `file_list.txt` |

---

## 🎯 Course Outcome Mapping

| Code | Outcome |
|------|---------|
| **CO1** | Familiarity with Linux system internals and file system concepts |
| **CO3** | Execution and manipulation of command output using redirection, piping, and process control |

---

## 📚 Learning Outcomes

After completing this experiment, the student will be able to:

- **LO1** — Understand and interpret inode information of files
- **LO2** — Use input and output redirection for managing command data
- **LO3** — Combine commands using pipes for advanced output processing
- **LO4** — Monitor and control running processes in Linux

---

## 📖 Theory

### Inodes

An **inode** is a data structure that stores metadata of a file such as:

| Metadata | Description |
|----------|-------------|
| File size | Size of the file in bytes |
| Ownership | User and group who own the file |
| Permissions | Read, write, execute access flags |
| Timestamps | Access, modify, and change times |
| Disk location | Physical block address on disk |

> File **names** are stored separately in directory entries and merely point to inodes. The inode itself has no knowledge of the filename.

---

### I/O Redirection

Redirection changes the standard input, output, or error streams:

| Operator | Description |
|----------|-------------|
| `>` | Redirect output (overwrite) |
| `>>` | Redirect output (append) |
| `<` | Redirect input |
| `2>` | Redirect error output |

---

### Pipes

Pipes (`|`) pass the output of one command directly as input to another:

```bash
ls | grep ".txt"
```

> Chains commands together for powerful, flexible output processing without creating intermediate files.

---

### Process Control

Linux supports multitasking. Processes can be monitored and controlled using:

| Command | Description |
|---------|-------------|
| `ps` | Display currently running processes |
| `top` | Real-time process monitoring |
| `kill` | Terminate a process by PID |
| `jobs` | List background jobs |
| `bg` | Resume a job in the background |
| `fg` | Bring a background job to the foreground |

---

## 🧪 Commands & Observations

### Part A — Understanding Inodes

#### 1. Create a Test File

```bash
touch inode_test.txt
```

> Creates an empty file. Linux immediately allocates an inode to store its metadata.

---

#### 2. Display Inode Number

```bash
ls -i inode_test.txt
```

**Output:**
```
134306 inode_test.txt
```

> The `-i` flag shows the inode number. Here `inode_test.txt` is assigned inode **134306**.

---

#### 3. View Detailed Inode Information

```bash
stat inode_test.txt
```

**Output:**
```
  File: inode_test.txt
  Size: 0           Blocks: 0          IO Block: 4096   regular empty file
Device: 8,1         Inode: 134306      Links: 1
Access: (0664/-rw-rw-r--)  Uid: ( 1000/  skde)   Gid: ( 1000/  skde)
Access: 2026-04-24 13:42:17.186073949 +0530
Modify: 2026-04-24 13:42:17.186073949 +0530
Change: 2026-04-24 13:42:17.186073949 +0530
 Birth: 2026-04-24 13:42:17.186073949 +0530
```

| Field | Value | Meaning |
|-------|-------|---------|
| Inode | 134306 | Unique identifier for this file |
| Size | 0 bytes | File is empty |
| Links | 1 | One directory entry points to this inode |
| Permissions | `0664 / -rw-rw-r--` | Owner & group can read/write; others read-only |
| Uid / Gid | 1000 / skde | Owned by user `skde` |
| Access | 2026-04-24 | Last time file was read |
| Modify | 2026-04-24 | Last time file content changed |
| Change | 2026-04-24 | Last time inode metadata changed |

---

### Part B — I/O Redirection

#### 4. Redirect Output to a File (`>`)

```bash
ls > file_list.txt
```

> Captures the output of `ls` and writes it into `file_list.txt`, **overwriting** any previous content.

---

#### 5. Append Output to a File (`>>`)

```bash
date >> file_list.txt
```

> Appends the current date and time to `file_list.txt` without erasing existing content.

---

#### 6. Redirect Input (`<`)

```bash
wc -l < file_list.txt
```

**Output:**
```
18
```

> `wc -l` counts lines. Using `<` feeds `file_list.txt` as input, reporting **18 lines** in the file.

> ⚠️ **Error Encountered:** `wc-l` (without space) returned `command not found`. The correct syntax is `wc -l` with a space between the command and flag.

---

### Part C — Using Pipes

#### 7. Filter Files Using Pipe

```bash
ls -l | grep ".txt"
```

**Output:**
```
-rw-rw-r-- 1 skde skde 227 Apr 24 13:46 file_list.txt
-rw-rw-r-- 1 skde skde   0 Apr 24 13:42 inode_test.txt
```

> The output of `ls -l` is piped into `grep`, which filters and displays only lines containing `.txt`.

---

#### 8. Count Number of Text Files

```bash
ls | grep ".txt" | wc -l
```

**Output:**
```
2
```

> A three-command pipeline: `ls` lists all files → `grep` filters `.txt` files → `wc -l` counts the results. There are **2** `.txt` files in the directory.

---

### Part D — Process Control Commands

#### 9. Display Running Processes

```bash
ps
```

**Output:**
```
  PID TTY          TIME CMD
 2327 pts/1    00:00:00 bash
 2594 pts/1    00:00:00 ps
```

> Shows all processes running in the current terminal session. `bash` (PID 2327) is the shell and `ps` (PID 2594) is the command itself.

---

#### 10. Run a Process in the Background

```bash
sleep 60 &
```

**Output:**
```
[1] 2597
```

> The `&` operator sends `sleep 60` to the background. The shell displays `[1]` (job number) and `2597` (PID), then immediately returns the prompt.

---

#### 11. List Background Jobs

```bash
jobs
```

**Output:**
```
[1]+  Running    sleep 60 &
```

> Confirms `sleep 60` is running as job `[1]` in the background.

---

#### 12. Bring Job to Foreground

```bash
fg
```

**Output:**
```
sleep 60
^C
```

> `fg` brings the background job to the foreground. `^C` (Ctrl+C) was used to manually interrupt and terminate it.

---

#### 13. Verify Processes After Interrupt

```bash
ps
```

**Output:**
```
  PID TTY          TIME CMD
 2327 pts/1    00:00:00 bash
 2651 pts/1    00:00:00 ps
```

> The `sleep` process no longer appears, confirming it was terminated successfully.

---

#### 14. Terminate a Process by PID

```bash
kill 2327
```

> Sends the default `SIGTERM` signal to PID 2327 (`bash`), requesting it to terminate gracefully.

---

## 📋 Command Summary

| Command | Description |
|---------|-------------|
| `touch inode_test.txt` | Create an empty test file |
| `ls -i inode_test.txt` | Display inode number of a file |
| `stat inode_test.txt` | View full inode metadata |
| `ls > file_list.txt` | Redirect `ls` output to file (overwrite) |
| `date >> file_list.txt` | Append date to file |
| `wc -l < file_list.txt` | Count lines using input redirection |
| `ls -l \| grep ".txt"` | Pipe to filter `.txt` files |
| `ls \| grep ".txt" \| wc -l` | Count `.txt` files using pipe chain |
| `ps` | Display current processes |
| `sleep 60 &` | Run process in background |
| `jobs` | List background jobs |
| `fg` | Bring background job to foreground |
| `kill <PID>` | Terminate a process by PID |

---

## ⚠️ Errors Encountered

```bash
wc-l < file_list.txt
# wc-l: command not found
```

> `wc-l` was typed without a space. Linux interpreted it as a single unknown command. Corrected to `wc -l < file_list.txt`, which returned `18` successfully.

---

## ✅ Expected Output

- Inode number and file metadata displayed correctly
- Command output redirected and appended to `file_list.txt` successfully
- Pipes used to filter `.txt` files and count them (result: `2`)
- `sleep 60` ran in the background, listed via `jobs`, brought to foreground with `fg`, and terminated with `^C`
- Process list verified before and after termination using `ps`

---

## 📌 Result

Inode information, input/output redirection, piping, and process control commands were successfully executed. Practical understanding of Linux file system internals and process management was demonstrated through hands-on terminal operations.

---

## ⚠️ Guidelines & Best Practices

- **Never kill critical system processes** — terminating essential PIDs can crash the system
- Use `kill -9 <PID>` only as a last resort (force kill); prefer `kill <PID>` for graceful termination
- Always include a **space** between a command and its flags (e.g., `wc -l`, not `wc-l`)
- Use `>>` instead of `>` when appending to avoid accidentally overwriting files
- Use pipes carefully to avoid unintended data loss or incorrect filtering
- Use `jobs` before `fg` to confirm which background job will be brought forward

---

*Experiment conducted on VMware Virtual Platform | Linux Bash Shell*
