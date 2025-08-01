---
tags: Linux, Utils, sed, text
alias: []
created: 2025-08-01
updated: 2025-08-01
source:
---

# `sed` Command Note
`sed` (Stream Editor) is a powerful command-line utility for parsing and transforming text. It reads text line-by-line from a file or input stream, applies a set of commands, and prints the result to standard output.

For more advanced usage, see [[sed_advanced]].

## Command Basic Usage

The most common `sed` command is `s` for substitution.

Command format:
```bash
sed 's/pattern/replacement/' [file...]
```

- **`s`**: The substitute command.
- **`pattern`**: A regular expression to match.
- **`replacement`**: The string to replace the matched pattern with.

### Basic Examples:

**1. Replacing Text in a File**
```bash
# Create a sample file
echo "Hello world" > greeting.txt
echo "This is a test world" >> greeting.txt

# Replace the first occurrence of 'world' with 'galaxy' on each line
sed 's/world/galaxy/' greeting.txt
```

**2. Replacing All Occurrences**

Add the `g` flag to replace all occurrences of the pattern on a line.
```bash
# Create a sample file
echo "test test test" > test.txt

# Replace all instances of 'test' with 'exam'
sed 's/test/exam/g' test.txt
```

**3. In-place Editing**

Use the `-i` option to modify the file directly.

```bash
# Directly modify greeting.txt, replacing 'Hello' with 'Hi'
sed -i 's/Hello/Hi/' greeting.txt

# Create a backup before editing
sed -i.bak 's/Hi/Greetings/' greeting.txt
# This creates greeting.txt.bak with the original content
```

**4. Deleting Lines**

The `d` command deletes lines that match a pattern.
```bash
# Delete lines containing the word 'test'
sed '/test/d' greeting.txt
```
