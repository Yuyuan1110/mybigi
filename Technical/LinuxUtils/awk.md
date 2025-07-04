---
tags: Linux, Utils, awk, text
alias: []
created: 2025-07-02
updated:
source:
---

# `awk` Command Note
`awk` is a powerful command-line tool that acts as a **pattern scanning and processing language**. It's primarily used for **data extraction and reporting** based on fields (columns) within a text file or stream.
## Command Basic Usage
`awk` works by reading input line by line, splitting each line into fields, and then performing actions based on patterns or conditions.
Command format:
```bash
awk [options] 'pattern { action }' [file...]
```

Option:
`-F`: it can specify using which charcter to split in a line, default is space " ".

## Common `awk` built-in variables

`awk` provides special variables for easy data manipulation:

- **`$0`**: Represents the **entire line** being processed.
    
- **`$1`, `$2`, `$3`, ...**: Represent the **first, second, third, etc., fields** of the current line.
    
- **`NF` (Number of Fields)**: The total **number of fields** in the current line.
    
- **`NR` (Number of Records)**: The **current line number** (record number) being processed.
    
- **`FS` (Field Separator)**: The **input field separator**. By default, it's any whitespace (spaces, tabs). Can be changed using `-F` option or `BEGIN {FS="..."}`.
    
- **`OFS` (Output Field Separator)**: The **output field separator** when using `print` with comma-separated fields. Default is a space.
    
- **`BEGIN`**: A special pattern. Actions in `BEGIN {}` are executed **once before** `awk` starts processing any input lines. Useful for printing headers or initializing variables.
    
- **`END`**: A special pattern. Actions in `END {}` are executed **once after** `awk` has processed all input lines. Useful for printing summaries or totals.

## Example `awk` usages

### 1. Printing specific fields

Bash

```
# Print the second field of each line from 'data.txt'
awk '{print $2}' data.txt

# Print the first and third fields, separated by a comma
echo "apple 10 red" | awk '{print $1 "," $3}' # Output: apple,red
```

### 2. Changing the field separator

Use the **`-F` option** to specify a different input field separator.

Bash

```
# Process a CSV file (comma-separated), printing the first and third fields
awk -F',' '{print $1, $3}' employees.csv

# Also set the output field separator to a comma
awk -F',' 'BEGIN {OFS=","} {print $1, $3}' employees.csv
```

### 3. Filtering lines based on conditions

`awk` can filter lines using patterns or conditional expressions.

Bash

```
# Print lines that contain the word "error" (if no action, defaults to print $0)
awk '/error/' access.log

# Print lines where the number of fields is greater than 5
awk 'NF > 5 {print $0}' long_lines.txt

# Print lines where the first field is exactly "root"
awk '$1 == "root" {print}' /etc/passwd
```

### 4. Performing calculations and summaries

`awk` excels at numerical processing and generating reports.

Bash

```
# Calculate the sum of the third column in 'numbers.txt'
# numbers.txt example:
# itemA 1 10
# itemB 2 20
# itemC 3 30
awk 'BEGIN {sum = 0} {sum += $3} END {print "Total sum:", sum}' numbers.txt # Output: Total sum: 60

# Count the number of lines containing "WARNING"
awk '/WARNING/ {count++} END {print "Warnings found:", count}' syslog.log
```

### 5. Using `BEGIN` and `END` blocks for headers and footers

Bash

```
# Print a header, then line number and content for each line, then a footer with total lines
awk 'BEGIN {print "--- File Content ---"} {print NR, $0} END {print "--- End of File, Total Lines:", NR, "---"}' my_file.txt
```

---

`awk` is incredibly versatile for structured text processing. If you have specific data manipulation tasks, `awk` is often the tool of choice over `grep` or `sed` when column-based logic, calculations, or more complex programming constructs are involved.
