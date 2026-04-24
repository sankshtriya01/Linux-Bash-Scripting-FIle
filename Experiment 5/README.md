# 🔍 Experiment 5: Linux `grep` Command Lab

A hands-on experiment exploring the `grep` and `fgrep` commands on a Raspberry Pi running Linux. This lab demonstrates pattern searching, case-insensitive matching, line numbering, inverted search, and recursive file searching.

-----

## 🖥️ Environment

|Property             |Value          |
|---------------------|---------------|
|**Platform**         |Raspberry Pi OS|
|**Shell**            |Bash           |
|**Working Directory**|`~/grep_lab`   |
|**Test File**        |`sample.txt`   |

-----

## 📄 Sample File Contents

The file `sample.txt` was created using `nano` and contains the following lines:

```
Linux is powerful
Linux is secure
Bash scripting is useful
Cyber Security uses Linux
```

-----

## 🧪 Commands & Observations

### 1. Basic Search with `grep`

```bash
grep Linux sample.txt
```

**Output:**

```
Linux is powerful
Linux is secure
Cyber Security uses Linux
```

> Returns all lines containing the exact string `Linux` (case-sensitive). The matching word is highlighted in the terminal output.

-----

### 2. Case-Insensitive Search with `grep -i`

```bash
grep -i linux sample.txt
```

**Output:**

```
Linux is powerful
Linux is secure
Cyber Security uses Linux
```

> The `-i` flag makes the search case-insensitive. Both `linux` and `Linux` are matched, returning the same results here since the file only uses `Linux`.

-----

### 3. Display Line Numbers with `grep -n`

```bash
grep -n Linux sample.txt
```

**Output:**

```
1:Linux is powerful
2:Linux is secure
4:Cyber Security uses Linux
```

> The `-n` flag prepends each matching line with its line number. Notice line 3 (`Bash scripting is useful`) is skipped as it does not contain `Linux`.

-----

### 4. Inverted Search with `grep -v`

```bash
grep -v Linux sample.txt
```

**Output:**

```
Bash scripting is useful
```

> The `-v` flag inverts the match — it returns all lines that do **not** contain the pattern `Linux`.

-----

### 5. Fixed String Search with `fgrep`

```bash
fgrep "Bash scripting" sample.txt
```

**Output:**

```
Bash scripting is useful
```

> `fgrep` (fixed-string grep) searches for a literal string without interpreting regex special characters. Useful when the search pattern contains characters like `.`, `*`, or `?`.

-----

### 6. Recursive Search with `grep -r`

```bash
grep -r Linux
```

**Output:**

```
sample.txt:Linux is powerful
sample.txt:Linux is secure
sample.txt:Cyber Security uses Linux
```

> The `-r` flag searches recursively through all files in the current directory. The output includes the filename prefix (`sample.txt:`) before each matching line.

-----

## 📋 Command Summary

|Command                            |Flag            |Description                           |
|-----------------------------------|----------------|--------------------------------------|
|`grep Linux sample.txt`            |*(none)*        |Basic case-sensitive search           |
|`grep -i linux sample.txt`         |`-i`            |Case-insensitive search               |
|`grep -n Linux sample.txt`         |`-n`            |Show line numbers with matches        |
|`grep -v Linux sample.txt`         |`-v`            |Invert match (show non-matching lines)|
|`fgrep "Bash scripting" sample.txt`|*(fixed string)*|Literal string search, no regex       |
|`grep -r Linux`                    |`-r`            |Recursive search across all files     |

-----

## ⚠️ Errors Encountered

```bash
cat file1.txt
# cat: file1.txt: No such file or directory
```

> Attempted to read a file `file1.txt` that did not exist in the directory. This is a common error when referencing incorrect filenames.

-----

## 🔑 Key Takeaways

- `grep` is a powerful tool for searching text patterns within files.
- The `-i` flag enables case-insensitive matching.
- The `-n` flag is useful for identifying exact line locations of matches.
- The `-v` flag is helpful for filtering out unwanted lines.
- `fgrep` is preferred over `grep` when searching for literal strings containing special characters.
- The `-r` flag allows searching across multiple files in a directory tree.

-----

## 📁 Lab Structure

```
~/grep_lab/
└── sample.txt
```

-----

*Experiment conducted on Raspberry Pi | Linux Bash Shell*
