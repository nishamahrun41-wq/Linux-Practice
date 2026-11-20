# Linux User, Group & Permission Management

A hands-on documentation and quick-reference repository covering essential Linux system administration commands for user onboarding, group membership management, and file/directory ownership and permissions.

---

## Overview

Managing users, groups, and access controls is a core responsibility in Linux environments. This repository documents the fundamental commands required to:
- Provision local user accounts with dedicated home directories and login shells
- Manage primary and supplementary group memberships
- Inspect user identities and system databases
- Create files/directories and configure ownership and permissions

---

## Command Reference

### 1. User & Group Provisioning

| Command | Purpose | Common Flags & Usage |
| :--- | :--- | :--- |
| `sudo` | Execute commands with superuser (`root`) privileges | `sudo <command>` (required for modifying system users/groups) |
| `useradd` | Create a new local user account | `sudo useradd -m -U -s /bin/bash <username>`<br>• `-m`: Create home directory (`/home/<username>`)<br>• `-U`: Create a matching private primary group<br>• `-s`: Set the default login shell |
| `usermod` | Modify an existing user account | `sudo usermod -aG <group> <username>`<br>• `-aG`: **Append** (`-a`) user to supplementary group (`-G`) without overwriting existing groups |
| `newgrp` | Switch current session's active primary group | `newgrp <group>` (applies new group membership immediately without logging out) |

### 2. Identity & System Database Verification

| Command | Purpose | Common Flags & Usage |
| :--- | :--- | :--- |
| `id` | Display real and effective user ID (`UID`), primary group (`GID`), and supplementary groups | `id` (current user) or `id <username>` |
| `getent` | Query entries from Name Service Switch (NSS) databases (`passwd`, `group`, etc.) | `getent passwd <username>`<br>`getent group <group>` |

### 3. File Creation, Ownership & Permissions

| Command | Purpose | Common Flags & Usage |
| :--- | :--- | :--- |
| `touch` | Create an empty file or update file timestamps | `touch <filename>` |
| `mkdir` | Create new directories | `mkdir <dir>` or `mkdir -p <parent>/<child>` |
| `chown` | Change file or directory user and group ownership | `sudo chown <user>:<group> <path>`<br>• `-R`: Apply recursively to directories and contents |
| `chmod` | Change file or directory access permissions | `chmod 750 <dir>` or `chmod g+w <file>`<br>• Numeric (`755`, `640`) or symbolic (`u+x`, `g+rw`, `o-rwx`) modes |

---

## Practical Workflow: Onboarding a Developer

Below is a complete end-to-end workflow demonstrating how these commands work together when onboarding a new team member (`trainee`) into a shared `developers` workspace.

### Step 1: Create the User & Assign Supplementary Group
```bash
# Create user 'trainee' with a home directory, private group, and Bash shell
sudo useradd -m -U -s /bin/bash trainee

# Append 'trainee' to the existing 'developers' group
sudo usermod -aG developers trainee
