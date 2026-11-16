# Module 3: OverTheWire Bandit Walkthrough (Levels 7 – 10)

---

## 1. Text Searching & Data Filtering

- **Level 7 → 8: Keyword Search in Large Files**
  - **Goal:** Locate the password stored in `data.txt` directly next to the word `millionth`.
  - **Details:** Use `grep` to filter lines matching a specific text pattern rather than reading massive files manually.

- **Level 8 → 9: Sorting & Finding Unique Lines**
  - **Goal:** Find the single line of text in `data.txt` that occurs only once.
  - **Details:** Combine `sort` and `uniq -u` via piping (`|`), as `uniq` only detects duplicates when identical lines are adjacent.

- **Level 9 → 10: Extracting Strings from Binary Data**
  - **Goal:** Extract a human-readable password preceded by several `=` characters inside a binary/mixed `data.txt` file.
  - **Details:** Use `strings` to isolate printable ASCII text sequences from non-text data, then pipe to `grep` to match the `==` prefix.

---

## Section Code Examples

```bash
# --- Level 7 -> 8 ---
# Search for the line containing the keyword 'millionth'
grep "millionth" data.txt
# Output: millionth    [bandit8_password]

# --- Level 8 -> 9 ---
# Sort lines alphabetically so duplicates are adjacent, then print only the unique line (-u)
sort data.txt | uniq -u
# Output: [bandit9_password]

# --- Level 9 -> 10 ---
# Extract human-readable strings from binary data and filter for '=' prefixes
strings data.txt | grep "=="
# Output: ========== [bandit10_password]
