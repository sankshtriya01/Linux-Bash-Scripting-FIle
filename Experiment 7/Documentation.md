# 👥 Experiment 7: Linux User & Group Management Lab

A hands-on experiment exploring user creation, group management, directory permissions, and file ownership on a Raspberry Pi running Linux. This lab demonstrates how to manage users, assign groups, configure shared directories, and set file ownership using standard Linux commands.

-----

## 🖥️ Environment

|Property              |Value       |
|----------------------|------------|
|**Platform**          |Raspberry Pi OS|
|**Shell**             |Bash        |
|**Primary User**      |`sk`        |
|**Test User Created** |`testuser`  |
|**Test Group Created**|`testgroup` |

-----

## 🧪 Commands & Observations

### 1. Create a New User

```bash
sudo useradd testuser
```

> Creates a new system user named `testuser`. The `sudo` prefix is required as user management needs root privileges.

-----

### 2. Set Password for New User

```bash
sudo passwd testuser
```

**Output:**

```
New password:
Retype new password:
passwd: password updated successfully
```

> Sets a password for `testuser`. The terminal prompts for password entry twice for confirmation.

-----

### 3. Verify User Identity

```bash
id testuser
```

**Output:**

```
uid=1001(testuser) gid=1001(testuser) groups=1001(testuser)
```

> Displays the User ID (`uid`), primary Group ID (`gid`), and all group memberships for `testuser`. The system auto-assigned `uid=1001` and `gid=1001`.

-----

### 4. Create a New Group

```bash
sudo groupadd testgroup
```

> Creates a new group named `testgroup`. Groups are used to manage shared permissions across multiple users.

-----

### 5. Add User to Group

```bash
sudo usermod -aG testgroup testuser
```

> The `-aG` flag **appends** `testuser` to `testgroup` without removing them from existing groups. Omitting `-a` would replace all current group memberships.

-----

### 6. Verify Group Membership

```bash
groups testuser
```

**Output:**

```
testuser : testuser testgroup
```

> Confirms that `testuser` now belongs to both their default group (`testuser`) and the newly added `testgroup`.

-----

### 7. Create a Shared Directory

```bash
mkdir shared_dir
```

> Creates a new directory named `shared_dir` in the current working directory.

-----

### 8. Assign Group Ownership to Directory

```bash
sudo chgrp testgroup shared_dir
```

> Changes the group ownership of `shared_dir` to `testgroup`, allowing all group members to access it based on group permissions.

-----

### 9. Set Directory Permissions

```bash
sudo chmod 770 shared_dir
```

> Sets permissions so the **owner** and **group** have full read, write, and execute access (`rwx`), while **others** have no access (`---`).

|Entity|Permission|Meaning    |
|------|----------|-----------|
|Owner |`rwx` (7) |Full access|
|Group |`rwx` (7) |Full access|
|Others|`---` (0) |No access  |

-----

### 10. Set the Sticky Bit

```bash
sudo chmod +t shared_dir
```

> The sticky bit (`+t`) prevents users from deleting or renaming files owned by others inside the shared directory — even if they have write permission. Commonly used on shared directories like `/tmp`.

-----

### 11. Verify Directory Permissions

```bash
ls -l
```

**Relevant Output (first listing):**

```
drwxrwx--T 2 sk testgroup 4096 Feb 20 13:58 shared_dir
```

> The `T` at the end of the permission string confirms the sticky bit is set. The group is now `testgroup` and permissions show `770`.

-----

### 12. Assign File Ownership (with Error)

```bash
sudo chown testuser:testgroup shared_file.txt
```

**Output:**

```
chown: cannot access 'shared_file.txt': No such file or directory
```

> Failed because `shared_file.txt` did not exist yet. The file must be created before ownership can be assigned.

-----

### 13. Create the File

```bash
touch shared_file.txt
```

> Creates an empty file named `shared_file.txt` in the current directory.

-----

### 14. Assign File Ownership (Successful)

```bash
sudo chown testuser:testgroup shared_file.txt
```

> Successfully sets the **owner** of `shared_file.txt` to `testuser` and the **group** to `testgroup`.

-----

### 15. Final Directory Listing

```bash
ls -l
```

**Relevant Output (final listing):**

```
drwxrwx--T 2 sk        testgroup  4096 Feb 20 13:58 shared_dir
-rw-rw-r-- 1 testuser  testgroup     0 Feb 20 14:02 shared_file.txt
```

> Confirms:
> 
> - `shared_dir` is owned by `sk`, group `testgroup`, with `770` permissions and sticky bit (`T`).
> - `shared_file.txt` is owned by `testuser`, group `testgroup`, with `664` permissions (`rw-rw-r--`).

-----

## 📋 Command Summary

|Command                                        |Description                                      |
|-----------------------------------------------|-------------------------------------------------|
|`sudo useradd testuser`                        |Create a new user                                |
|`sudo passwd testuser`                         |Set password for a user                          |
|`id testuser`                                  |Display user ID and group memberships            |
|`sudo groupadd testgroup`                      |Create a new group                               |
|`sudo usermod -aG testgroup testuser`          |Append user to a group                           |
|`groups testuser`                              |List all groups a user belongs to                |
|`mkdir shared_dir`                             |Create a new directory                           |
|`sudo chgrp testgroup shared_dir`              |Change group ownership of a directory            |
|`sudo chmod 770 shared_dir`                    |Set owner/group full access, block others        |
|`sudo chmod +t shared_dir`                     |Set sticky bit on directory                      |
|`touch shared_file.txt`                        |Create an empty file                             |
|`sudo chown testuser:testgroup shared_file.txt`|Set file owner and group                         |
|`ls -l`                                        |List files with permissions and ownership details|

-----

## ⚠️ Errors Encountered

```bash
sudo chown testuser:testgroup shared_file.txt
# chown: cannot access 'shared_file.txt': No such file or directory
```

> Attempted to change ownership of a file that had not been created yet. Resolved by first creating the file with `touch shared_file.txt`, then re-running the `chown` command successfully.

-----

## 🔑 Key Takeaways

- `useradd` and `passwd` are used together to create and secure new user accounts.
- `usermod -aG` safely appends a user to a group without removing existing memberships.
- `chgrp` changes group ownership; `chown` changes both user and group ownership.
- `chmod 770` restricts directory access to the owner and group only.
- The **sticky bit** (`+t`) protects files in shared directories from deletion by non-owners.
- Always create a file before attempting to assign ownership to it.

-----

## 📁 Lab Directory Structure

```
~/
├── shared_dir/          # drwxrwx--T (owner: sk, group: testgroup)
└── shared_file.txt      # -rw-rw-r-- (owner: testuser, group: testgroup)
```

-----

## 🔐 Permission Reference

```
d rwx rwx --- T
│  │   │   │  └── Sticky bit (T = set, no execute for others)
│  │   │   └───── Others: no permission
│  │   └───────── Group: read, write, execute
│  └───────────── Owner: read, write, execute
└──────────────── d = directory, - = file
```

-----

*Experiment conducted on Raspberry Pi | Linux Bash Shell*
