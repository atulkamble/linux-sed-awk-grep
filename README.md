**`sed`**, **`awk`**, and **`grep`**, three of the most powerful and frequently used text processing utilities in Linux/Unix environments.

---

## 📌 `grep` — **Global Regular Expression Print**

* **Purpose**: Search for lines in a file or input stream that match a given pattern.

* **Syntax**:

  ```bash
  grep 'pattern' filename
  ```

* **Example**:

  ```bash
  grep "error" /var/log/syslog
  ```

  👉 Displays all lines containing the word `error` from `/var/log/syslog`.

* **Common options**:

  * `-i` : Case-insensitive search
  * `-v` : Invert match (show lines not matching)
  * `-n` : Show line numbers
  * `-r` : Recursive search in directories

---

## 📌 `sed` — **Stream Editor**

* **Purpose**: Perform text transformations on an input stream (files or pipelines).

* **Syntax**:

  ```bash
  sed 's/pattern/replacement/' filename
  ```
  ```
  sed 's/hello/good morning/g' a.txt
  ```

* **Example**:

  ```bash
  sed 's/oldword/newword/g' file.txt
  ```

  👉 Replaces all occurrences of `oldword` with `newword` in `file.txt`.

* **Common actions**:

  * `s` : Substitute
  * `d` : Delete lines
  * `p` : Print lines
  * `-i` : Edit file in-place

* **Example: Remove empty lines**

  ```bash
  sed '/^$/d' file.txt
  ```

---

## 📌 `awk` — **Pattern Scanning and Processing Language**

* **Purpose**: Process and analyze structured text, typically splitting data by fields (columns).

* **Syntax**:

  ```bash
  awk 'pattern { action }' filename
  ```

* **Example**:

  ```bash
  awk '{print $1}' file.txt
  ```

  👉 Prints the first field (word/column) of each line in `file.txt`.

* **Common uses**:

  * Extracting columns
  * Summing values
  * Applying conditions
  * Formatting output

* **Example: Sum values in 3rd column**

  ```bash
  awk '{sum+=$3} END {print sum}' file.txt
  ```

---

## 📊 Summary Table:

| Tool   | Primary Use                      | Input Style        | Key Strength                |
| :----- | :------------------------------- | :----------------- | :-------------------------- |
| `grep` | Find lines matching a pattern    | Line by line       | Fast pattern searching      |
| `sed`  | Replace/edit text in streams     | Line by line       | Simple substitutions        |
| `awk`  | Process fields & structured data | Field/record based | Reporting and text analysis |

---

## 🔗 Practical Combined Example:

**Extract error lines from a log, replace IP addresses with `[REDACTED]`, and print the 5th field:**

```bash
grep "ERROR" logfile.log | sed 's/[0-9]\+\.[0-9]\+\.[0-9]\+\.[0-9]\+/\[REDACTED\]/g' | awk '{print $5}'
```

---
