# 📁 Experiment 4: Linux File Operations & I/O Redirection Lab

Efficient file management is a critical requirement in Linux-based systems, especially for system administrators and cybersecurity professionals. This experiment practices Linux commands for creating, copying, moving, renaming, deleting, and displaying files — along with input/output redirection for managing command outputs.

-----

## 🖥️ Environment

|Property             |Value                  |
|---------------------|-----------------------|
|**Platform**         |VMware Virtual Platform|
|**Shell**            |Bash                   |
|**User**             |`skde`                 |
|**Working Directory**|`~/file_ops`           |

-----

## 🎯 Course Outcome Mapping

|Code   |Outcome                                                                         |
|-------|--------------------------------------------------------------------------------|
|**CO1**|Familiarity with Linux environment, command-line interface, and system utilities|
|**CO3**|Manipulation of command outputs using redirection                               |

-----

## 📚 Learning Outcomes

After completing this experiment, the student will be able to:

- **LO1** — Create and manage files using Linux commands
- **LO2** — Copy, move, rename, and delete files safely
- **LO3** — Display file contents using command-line tools
- **LO4** — Use input/output redirection to store command output in files

-----

## 📖 Theory

### File Management Commands

Linux offers several commands to manage files:

|Command|Description                |
|-------|---------------------------|
|`touch`|Create empty files         |
|`cp`   |Copy files or directories  |
|`mv`   |Move or rename files       |
|`rm`   |Delete files or directories|
|`cat`  |Display file contents      |

### Input/Output Redirection

Redirection allows command outputs to be sent to files instead of the terminal:

|Operator|Description                |
|--------|---------------------------|
|`>`     |Redirect output (overwrite)|
|`>>`    |Redirect output (append)   |
|`<`     |Redirect input             |


> These features are essential for scripting and automation in Linux environments.

-----

## 🧪 Commands & Observations

### 1. Create Working Directory & Navigate Into It

```bash
mkdir file_ops
cd file_ops
```

> Creates a new directory `file_ops` and changes into it as the working directory for this experiment.

-----

### 2. Create Empty Files

```bash
touch file1.txt file2.txt
```

> The `touch` command creates two empty files simultaneously. If the files already exist, it updates their timestamp.

-----

### 3. Add Content Using Output Redirection (`>`)

```bash
echo "This is file1" > file1.txt
echo "This is file2" > file2.txt
```

> The `>` operator redirects the output of `echo` into a file, **overwriting** any existing content. Each file now holds one line of text.

-----

### 4. Display File Contents

```bash
cat file1.txt
```

**Output:**

```
This is file1
```

> `cat` reads and prints the full content of a file to the terminal.

-----

### 5. Copy a File

```bash
cp file1.txt copy_file1.txt
```

> Creates an exact duplicate of `file1.txt` named `copy_file1.txt`. The original file remains unchanged.

-----

### 6. Rename a File

```bash
mv file2.txt renamed_file2.txt
```

> `mv` is used to rename files when the source and destination are in the same directory. `file2.txt` no longer exists — it is now `renamed_file2.txt`.

-----

### 7. Create a Backup Directory & Move a File Into It

```bash
mkdir backup
mv copy_file1.txt backup/
```

> Creates a `backup/` subdirectory and moves `copy_file1.txt` into it. The file is no longer in `file_ops/` — it now resides in `file_ops/backup/`.

-----

### 8. Append Content to a File (`>>`)

```bash
echo "Additional content" >> file1.txt
```

> The `>>` operator **appends** text to an existing file without overwriting. `file1.txt` now contains two lines:
> 
> ```
> This is file1
> Additional content
> ```

-----

### 9. Verify Contents After Append

```bash
cat file1.txt
```

**Output:**

```
This is file1
```

> *(Screenshot shows the state before appending; after appending, the second line would also appear.)*

-----

### 10. Delete a File

```bash
rm renamed_file2.txt
```

> Permanently deletes `renamed_file2.txt`. There is no recycle bin in Linux — this action is irreversible.

-----

### 11. Verify Final State

```bash
ls
```

**Output:**

```
backup   file1.txt
```

> Only `backup/` and `file1.txt` remain in the working directory, confirming all operations completed successfully.

-----

## 📋 Command Summary

|Command                         |Purpose                          |
|--------------------------------|---------------------------------|
|`mkdir file_ops`                |Create working directory         |
|`cd file_ops`                   |Navigate into directory          |
|`touch file1.txt file2.txt`     |Create empty files               |
|`echo "..." > file1.txt`        |Write content to file (overwrite)|
|`echo "..." >> file1.txt`       |Append content to file           |
|`cat file1.txt`                 |Display file contents            |
|`cp file1.txt copy_file1.txt`   |Copy a file                      |
|`mv file2.txt renamed_file2.txt`|Rename a file                    |
|`mkdir backup`                  |Create backup directory          |
|`mv copy_file1.txt backup/`     |Move file to another directory   |
|`rm renamed_file2.txt`          |Delete a file permanently        |
|`ls`                            |List files in current directory  |

-----

## ✅ Expected Output

- Files created, copied, renamed, and deleted successfully
- File contents displayed correctly using `cat`
- Output redirection (`>` and `>>`) works as expected
- Final `ls` shows only `backup/` and `file1.txt`

-----

## 📁 Final Directory Structure

```
~/file_ops/
├── backup/
│   └── copy_file1.txt
└── file1.txt
```

-----

## 📌 Result

Linux file operations including copying, moving, renaming, and deleting files, as well as output redirection (`>`, `>>`), were successfully performed using command-line utilities on a VMware Linux environment.

-----

## ⚠️ Guidelines & Best Practices

> ⚡ **Warning:** `rm` permanently deletes files with no recovery option. Always double-check before executing.

- Use `rm` carefully — deleted files **cannot** be easily recovered
- Verify file names before executing copy or delete commands
- Use `>` redirection cautiously to avoid overwriting important data
- Always maintain backups of critical files before performing bulk operations
- Use `ls` frequently to verify the state of your directory after each operation

-----

*Experiment conducted on VMware Virtual Platform | Linux Bash Shell*
