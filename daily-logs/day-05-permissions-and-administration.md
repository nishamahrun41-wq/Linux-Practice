# 📝 Day 5: Linux System Administration, Permissions & Advanced File Operations

## 📌 Overview
Today's lab focused on core Linux administration and file management tasks. The primary objectives were managing elevated privileges, configuring directory and file permission structures, establishing shared group environments, isolating sensitive files, and leveraging string searching tools for system verification.

---

## 🛠️ Key Commands & Concepts Practiced

### 1. Privilege Escalation (`sudo`)
* **Purpose**: Execute administrative tasks requiring superuser access without remaining logged in as `root`.
* **Usage**: Used to modify ownership and permissions on system-level directories and restricted files safely.

### 2. File Ownership (`chown`)
* **Purpose**: Change user and group ownership of files and directories.
* **Key Flags**:
  * `-R`: Applies ownership changes recursively across subdirectories and contained files.

### 3. File Permissions & Access Control (`chmod`)
* **Purpose**: Modify read (`r=4`), write (`w=2`), and execute (`x=1`) permissions for Owner, Group, and Others.
* **Special Modes**:
  * **SetGID Bit (`2xxx` or `g+s`)**: Applied to shared directories so newly created files automatically inherit the parent directory's group ownership rather than the creating user's primary group.

### 4. File Creation & Removal (`touch` & `rm`)
* **Purpose**:
  * `touch`: Create empty files or update file timestamps.
  * `rm`: Remove files or directories from the filesystem.

### 5. Text & Pattern Searching (`grep`)
* **Purpose**: Search plain-text data sets for lines matching regular expressions or specific text patterns to verify configurations and inspect logs.

---

## 💻 Lab Work & Execution Steps

### Step 1: Base Directory Access Control
Configured directory access on `~/project/phoenix_project` to grant full access to the owner, read/traverse access to group members, and block all other users:

```bash
sudo chmod 750 ~/project/phoenix_project
