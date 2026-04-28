# 🐧 Linux Lab Capstone Assignment

A hands-on Linux lab covering directory management, shell scripting, and file permissions.

-----

## 📁 Q1. Directory and File Management

**Objective:** Create and manage a directory structure using your `Name_RollNo` format.

### Steps

1. **Create the main directory**
   
   ```bash
   mkdir Sankarshan_2301410027
   cd Sankarshan_2301410027
   ```
1. **Create subdirectories**
   
   ```bash
   mkdir Docs Programs Backup
   ```
1. **Create files inside `Docs`**
   
   ```bash
   touch Docs/exp1.txt Docs/exp2.txt
   ```
1. **Copy `exp1.txt` into `Backup`**
   
   ```bash
   cp Docs/exp1.txt Backup/
   ```
1. **Rename `exp2.txt` to `labrecord.txt`**
   
   ```bash
   mv Docs/exp2.txt Docs/labrecord.txt
   ```
1. **Display the full directory structure**
   
   ```bash
   tree
   ```
   or
   ```bash
   ls -R
   ```

### Expected Structure

```
Sankarshan_2301410027/
├── Docs/
│   ├── exp1.txt
│   └── labrecord.txt
├── Programs/
└── Backup/
    └── exp1.txt
```

-----

## 🖊️ Q2. Shell Script Writing

**Objective:** Write and execute a shell script named `scriptA_RollNo.sh`.

### Script: `scriptA_2301410027.sh`

```bash
#!/bin/bash

# Accept student name as input
read -p "Enter your name: " student_name

# Display welcome message
echo "Welcome, $student_name!"

# Display current date and time
echo "Date & Time: $(date)"

# Display present working directory
echo "Working Directory: $(pwd)"

# Display logged-in username
echo "Logged in as: $(whoami)"
```

### How to Run

```bash
# Give execute permission
chmod +x scriptA_2301410027.sh

# Run the script
./scriptA_2301410027.sh
```

-----

## 🔐 Q3. Permissions & Text Commands

**Objective:** Create a file, set permissions, add content, and use text commands.

### Steps

1. **Create the file inside your main directory**
   
   ```bash
   touch data_2301410027.txt
   ```
1. **Give only the owner read/write permission**
   
   ```bash
   chmod 600 data_2301410027.txt
   ```
1. **Write 5 Linux commands into the file**
   
   ```bash
   ls > data_2301410027.txt << EOF
   ls - List directory contents
   pwd - Print working directory
   whoami - Prints username
   date - Shows date
   mkdir - Create directory
   EOF
   ```
1. **Display the file contents**
   
   ```bash
   cat data_2301410027.txt
   ```
1. **Count total lines in the file**
   
   ```bash
   wc -l data_2301410027.txt
   ```

-----

## 📋 Submission Checklist

- [ ] Main directory created in `Name_RollNo` format
- [ ] Subdirectories `Docs`, `Programs`, `Backup` created
- [ ] `exp1.txt` and `exp2.txt` created inside `Docs`
- [ ] `exp1.txt` copied to `Backup`
- [ ] `exp2.txt` renamed to `labrecord.txt`
- [ ] Directory structure displayed using `tree`
- [ ] Shell script `scriptA_RollNo.sh` written and executed successfully
- [ ] `data_RollNo.txt` created with `600` permissions
- [ ] 5 Linux commands written in the file
- [ ] File contents displayed and line count verified

-----

## 📝 Notes

- Replace `RollNo` with your actual roll number in all filenames and directory names.
- Ensure scripts have execute permission before running (`chmod +x`).
- Use `man <command>` to read the manual for any Linux command.
