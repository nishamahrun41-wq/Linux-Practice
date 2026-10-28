# 🐧 Linux Practice & Commands Log

Documenting my daily command-line exercises and shell scripting practice on [LabEx](https://labex.io/learn/linux).

---

## 📝 Practice Log: Basic Introductory Commands

### 1. User & Identity Commands
- `whoami` — Displays the username of the currently logged-in user.
- `id` — Displays user ID (`uid`), group ID (`gid`), and group memberships.
- `id -un` — Prints only the user name instead of the numeric ID.
- `id root` — Displays the user and group details specifically for the `root` administrative account.
- `uid` / `gid` / `groups` — View specific user, group ID numbers, and group affiliations.

### 2. Navigation & File Inspection
- `pwd` — Print Working Directory (shows your current location in the filesystem).
- `ls` — Lists files and directories in the current folder.
- `cd` — Change directory to navigate through the file system.
- `cat` — Outputs and displays the contents of a text file on the terminal.
- `file` — Determines the file type (e.g., ASCII text, executable, directory).
- `du` — Disk Usage (estimates file and directory space usage).

### 3. Searching & Filtering
- `find` — Searches for files and directories based on names, paths, or attributes.
- `grep` — Searches for specific text patterns inside files or command output.

### 4. Operators & I/O Redirection
- `>` — Redirects output to a file (overwrites existing file contents).
- `>>` — Appends output to the end of an existing file.
- `&` — Runs a command or process in the background.
- `&&` — Logical AND operator (runs the second command only if the first command succeeds).
