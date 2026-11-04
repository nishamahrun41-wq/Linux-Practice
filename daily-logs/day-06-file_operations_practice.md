# Day 06: Linux Terminal Basics & File Operations

## Overview
Today's focus was on initial terminal setup and mastering basic Linux commands for navigating directories and managing files.

---

## Core Commands Learned

### File & Directory Management
* **`touch`**: Creates new empty files or updates timestamps on existing files.
  * *Example:* `touch file1.txt file2.txt`
* **`cat`**: Displays file contents directly in the terminal or concatenates multiple files.
  * *Example:* `cat notes.txt`
* **`cd`**: Changes the current working directory path.
  * *Example:* `cd ~/documents`
* **`cp`**: Copies files or entire directories to a target location.
  * *Example:* `cp notes.txt backup_notes.txt`
* **`mv`**: Moves files to a new path or renames files in place.
  * *Example:* `mv file1.txt docs/`
* **`rm`**: Removes files or directories permanently.
  * *Example:* `rm temp.txt`

---

## Hands-on Execution Log

```bash
# Create directory structure for today's lab
mkdir -p ~/linux_practice/day06
cd ~/linux_practice/day06

# Create sample workspace files
touch sample.txt demo.txt temp.txt

# Add initial content and view it
echo "Practicing basic Linux file operations" > sample.txt
cat sample.txt

# File manipulation practice
mv demo.txt renamed_demo.txt
cp sample.txt sample_copy.txt

# Directory operations
mkdir -p project/data
cp -r project/ project_backup/
mv renamed_demo.txt project/

# Clean up temporary files
rm temp.txt
rm -rf project_backup/
