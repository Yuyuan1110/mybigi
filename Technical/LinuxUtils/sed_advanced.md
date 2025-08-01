---
tags: Linux, Utils, sed, text
alias: []
created: 2025-08-01
updated: 2025-08-01
source:
---

# `sed` Advanced Usage

This note covers more advanced `sed` features. For a basic introduction, see [[sed]].

## Multiple Commands

You can combine multiple `sed` commands using the `-e` option or by separating them with a semicolon.

```bash
# Using -e to run two substitution commands
sed -e 's/Hello/Hi/' -e 's/world/galaxy/' greeting.txt

# Using a semicolon to achieve the same result
sed 's/Hello/Hi/; s/world/galaxy/' greeting.txt
```

## Address Ranges

`sed` commands can be applied to specific lines or a range of lines.

```bash
# Apply substitution only on line 2
sed '2 s/test/exam/' greeting.txt

# Apply substitution from line 1 to line 3
sed '1,3 s/test/exam/' greeting.txt

# Apply substitution only on lines containing "Hello"
sed '/Hello/ s/world/galaxy/' greeting.txt
```

## Using Different Delimiters

When your pattern or replacement contains slashes (`/`), it's useful to change the delimiter to avoid excessive escaping.

```bash
# This is hard to read due to escaping the slashes
sed 's/path\/to\/file/new\/path\/to\/file/'

# This is much cleaner using a different delimiter (#)
sed 's#/path/to/file#/new/path/to/file#'
```

## Capturing Groups

You can capture parts of the pattern using parentheses `\( ... \)` and reference them in the replacement with `\1`, `\2`, etc.

```bash
# Swap the first two words of each line
echo "first second" | sed 's/\([^ ]*\) \([^ ]*\)/\2 \1/'
# Output: second first
```
