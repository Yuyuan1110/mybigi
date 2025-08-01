---
tags: Linux, Utils, awk, text
alias: []
created: 2025-08-01
updated: 2025-08-01
source:
---

# `awk` Advanced Usage

This note covers more advanced `awk` features. For a basic introduction, see [[awk]].

## Built-in Variables

`awk` provides special variables for more complex data manipulation:

- **`$0`**: The entire current line.
- **`$1`, `$2`, ...`**: The first, second, etc., fields.
- **`NF`**: The total **N**umber of **F**ields in the current line.
- **`NR`**: The **N**umber of the current **R**ecord (line number).
- **`FS`**: The **F**ield **S**eparator (default is whitespace). Can be changed with the `-F` option.
- **`OFS`**: The **O**utput **F**ield **S**eparator (default is a space).

## `BEGIN` and `END` Blocks

Special blocks for actions before and after processing:

- **`BEGIN {}`**: Executed **once before** any lines are read. Ideal for initializing variables or printing headers.
- **`END {}`**: Executed **once after** all lines are read. Ideal for calculations and summaries.

### Advanced Examples:

**1. Using `BEGIN` and `END` for a Report**

This example processes a file, adds a header, and calculates a total.

```bash
# Create a sample file
echo "item cost" > sales.txt
echo "book 15" >> sales.txt
echo "pen 2" >> sales.txt
echo "stapler 5" >> sales.txt

# Generate a report with a header, formatted output, and a total
awk '
  BEGIN { 
    FS=" "; OFS="\t";
    print "Item\tPrice"; 
    print "----------------";
    sum = 0; 
  }
  # Skip the header line in the file
  NR > 1 {
    print $1, "$" $2;
    sum += $2;
  }
  END { 
    print "----------------";
    print "Total", "$" sum;
  }
' sales.txt
```

**2. On-the-Fly Variable Assignment**

You can create and modify variables while processing.

```bash
# Add a line number to each line of a file
awk '{print NR, $0}' sales.txt

# Categorize items based on price
awk '
  NR > 1 {
    category = ($2 > 10) ? "Expensive" : "Affordable";
    print $1, category;
  }
' sales.txt
```

**3. Using `if-else` Statements**

For more complex conditions, you can use standard `if-else` logic.

```bash
# Print a custom message based on the content of the line
awk '
  /book/ { print "Found a book!"; }
  /pen/ { print "Found a pen!"; }
' sales.txt
```
