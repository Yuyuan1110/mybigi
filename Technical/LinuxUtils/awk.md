---
tags: Linux, Utils, awk, text
alias: []
created: 2025-07-02
updated: 2025-08-01
source:
---

# `awk` Command Note
`awk` is a powerful command-line tool that acts as a **pattern scanning and processing language**. It's primarily used for **data extraction and reporting** based on fields (columns) within a text file or stream.

For more advanced usage, see [[awk_advanced]].

## Command Basic Usage
`awk` works by reading input line by line, splitting each line into fields, and then performing actions based on patterns or conditions.

Command format:
```bash
awk [options] 'pattern { action }' [file...]
```

- **`pattern`**: A condition to select which lines to process. If omitted, `awk` processes all lines.
- **`{ action }`**: The command to execute on the selected lines. The default action is `{ print $0 }`, which prints the entire line.

### Option:
- **`-F <separator>`**: Specifies the input field separator. The default is any whitespace.

### Basic Examples:

**1. Printing Specific Fields**
```bash
# Create a sample file
echo "fruit count color" > data.txt
echo "apple 10 red" >> data.txt
echo "grape 25 green" >> data.txt

# Print the first field ($1) of each line
awk '{print $1}' data.txt

# Print the first and third fields, separated by a tab
awk '{print $1, "\t", $3}' data.txt
```

**2. Filtering Lines with a Pattern**
```bash
# Print lines containing the word "apple"
awk '/apple/' data.txt

# Print lines where the second field is greater than 15
awk '$2 > 15' data.txt
```

**3. Using a Different Field Separator**
```bash
# Create a CSV sample file
echo "name,dept,role" > employees.csv
echo "alice,sales,manager" >> employees.csv
echo "bob,eng,developer" >> employees.csv

# Process the CSV file, printing the name (field 1) and role (field 3)
awk -F',' '{print $1, $3}' employees.csv
```
