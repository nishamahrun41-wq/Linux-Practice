# Day 3: Linux User Account Management & File Permissions

## Overview
Today's learning focused on Linux user administration, group management, and understanding file permissions using both numeric (octal) and symbolic modes.

---

## Key Concepts & Commands

### 1. User & Group Administration
* `sudo useradd -m <username>` — Creates a new user account with a home directory.
* `sudo passwd <username>` — Sets or updates the user password.
* `sudo groupadd <groupname>` — Creates a new group.
* `sudo usermod -aG <groupname> <username>` — Appends a user to a secondary group without removing existing group memberships.

### 2. File Ownership Management
* `sudo chown <owner>:<group> <file>` — Changes both the user owner and group owner of a file.
* `sudo chown <owner> <file>` — Changes only the file owner.

### 3. File Permissions (`chmod`)
Permissions are divided into **Owner (u)**, **Group (g)**, and **Others (o)** using Read (**4**), Write (**2**), and Execute (**1**):
* `chmod 750 <file>` — **Numeric Mode:** Grants full access (`rwx`) to Owner, read/execute (`r-x`) to Group, and no access (`---`) to Others.
* `chmod 600 <file>` — Restricts file access strictly to Owner read/write (`rw-`).
* `chmod g+w <file>` — **Symbolic Mode:** Adds write access for the group.

### 4. File Operations & Inspection
* `mkdir` & `touch` — Creates directories and empty files.
* `ls -la` — Lists all files (including hidden ones) in long format showing permissions, ownership, and file sizes.

---

## Hands-On Practice

```bash
# 1. Create Users and Group
sudo useradd -m developer
sudo passwd developer
sudo groupadd devteam
sudo usermod -aG devteam developer

# 2. Directory and File Setup
mkdir ~/permission_lab && cd ~/permission_lab
touch project_notes.txt script.sh confidential.txt

# 3. Modify Ownership & Permissions
sudo chown developer:devteam project_notes.txt
chmod 750 script.sh
chmod g+w project_notes.txt
chmod 600 confidential.txt

# 4. Verification
ls -la
