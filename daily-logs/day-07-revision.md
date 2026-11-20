OverTheWire Bandit Walkthrough (Levels 0 – 7)

---

## 1. Connection & Core Concepts

- **Level 0: Server Connection**
  - **Goal:** Establish an SSH session with the remote lab server.
  - **Details:** Access `bandit.labs.overthewire.org` on port `2220` using user `bandit0`.

- **Level 0 → 1: Basic File Reading**
  - **Goal:** Locate and read the standard `readme` file in the home directory.
  - **Details:** Basic Linux navigation using standard file-viewing utilities like `cat`.

- **Level 1 → 2: Handling Special Filenames (Dashes)**
  - **Goal:** Read a file named `-`.
  - **Details:** Prefix filenames starting with a dash using explicit pathing (`./-`) to prevent tools from parsing them as command-line options.

- **Level 2 → 3: Filenames with Spaces**
  - **Goal:** Read a file named `spaces in this filename`.
  - **Details:** Use surrounding quotes or backslash escaping (`\ `) to process spaces in path arguments.

---

## 2. Directory Inspection & Searching

- **Level 3 → 4: Hidden Files**
  - **Goal:** Uncover hidden dotfiles inside the `inhere` folder.
  - **Details:** Use `ls -la` to display all entries, including files starting with a dot (`.`).

- **Level 4 → 5: File Type Identification**
  - **Goal:** Locate the single human-readable file in `inhere`.
  - **Details:** Use the `file` utility to inspect file encoding (ASCII text vs. binary data).

- **Level 5 → 6: Advanced File Attributes Search**
  - **Goal:** Search `inhere` for a non-executable, human-readable file exactly 1033 bytes in size.
  - **Details:** Filter directory trees using specific `find` flags (`-type f`, `-size 1033c`, `! -executable`).

- **Level 6 → 7: System-Wide Search & Error Redirection**
  - **Goal:** Locate a 33-byte file owned by user `bandit7` and group `bandit6` across the root filesystem.
  - **Details:** Perform system-wide queries with user/group filters while suppressing standard error outputs (`2>/dev/null`).

---

## Section Code Examples

```bash
# --- Level 0 ---
# Connect to the game server via SSH
ssh bandit0@bandit.labs.overthewire.org -p 2220
# Output: Authenticated to server (Password: bandit0)

# --- Level 0 -> 1 ---
# View standard readme file content
cat readme
# Output: [bandit1_password]

# --- Level 1 -> 2 ---
# Read file named '-' by preventing flag misinterpretation
cat ./-
# Output: [bandit2_password]

# --- Level 2 -> 3 ---
# Read file with spaces using escaping or quotes
cat "spaces in this filename"
# Output: [bandit3_password]

# --- Level 3 -> 4 ---
# List all hidden files and read the hidden content
cd inhere && ls -la
cat .hidden
# Output: [bandit4_password]

# --- Level 4 -> 5 ---
# Inspect file encodings to find ASCII text
file ./-*
cat ./-file07
# Output: ASCII text -> [bandit5_password]

# --- Level 5 -> 6 ---
# Search by exact size (1033 bytes) and non-executable property
find . -type f -size 1033c ! -executable
cat ./maybehere07/.file2
# Output: [bandit6_password]

# --- Level 6 -> 7 ---
# Search root directory for specific owner/group and discard permission errors
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
cat /var/lib/dpkg/info/bandit7.password
# Output: [bandit7_password]
