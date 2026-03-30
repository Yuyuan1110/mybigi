---
tags: 
  - Utils
  - Regex
  - TextProcessing
  - Regular
  - RE
  - Common
alias: [regex, RE]
created: 2025-08-01
updated:
source:
---

# Regular Expressions (Regex) Note

A Regular Expression (or Regex) is a sequence of characters that specifies a search pattern in text. It is an incredibly powerful tool for searching, matching, and manipulating strings.

Regex is used by many command-line tools (`grep`, `sed`, `awk`) and is a core feature in most programming languages.

---

## Core Concepts

### 1. Literals
The most basic regex consists of literal characters. The pattern `cat` will match the sequence of characters `c`, `a`, `t` anywhere in the text.

### 2. Metacharacters
Metacharacters are special characters that have a unique meaning in the regex engine. The most common ones are:

- **`.` (Dot)**: Matches any single character except a newline.
  - `c.t` matches `cat`, `cot`, `c@t`, etc.

- **`*` (Asterisk)**: Matches the preceding character **zero or more** times.
  - `colou*r` matches `color` and `colour`.

- **`+` (Plus)**: Matches the preceding character **one or more** times.
  - `coo+l` matches `cool` and `coool`, but not `col`.

- **`?` (Question Mark)**: Matches the preceding character **zero or one** time. It makes the character optional.
  - `colou?r` matches `color` and `colour`.

### 3. Anchors
Anchors match a position in the string, not a character.

- **`^` (Caret)**: Matches the beginning of a line.
  - `^Hello` matches a line that starts with `Hello`.

- **`$` (Dollar Sign)**: Matches the end of a line.
  - `world$` matches a line that ends with `world`.

### 4. Character Sets and Classes

- **`[]` (Square Brackets)**: Matches any single character within the brackets.
  - `[aeiou]` matches any vowel.
  - `[0-9]` matches any digit.
  - `[^0-9]` matches any character that is *not* a digit (when `^` is the first character inside the brackets).

- **`|` (Alternation / OR)**: Acts like a boolean OR.
  - `cat|dog` matches either `cat` or `dog`.

- **`()` (Grouping)**: Groups parts of a pattern together. This allows you to apply quantifiers to a whole group or to capture the matched text.
  - `(very )+` matches `very ` one or more times (e.g., `very very `).

### 5. Shorthand Character Classes

- **`\w`**: Matches any "word" character (alphanumeric characters `[a-zA-Z0-9]` plus underscore `_`).
- **`\W`**: Matches any non-word character.
- **`\d`**: Matches any digit (`[0-9]`).
- **`\D`**: Matches any non-digit.
- **`\s`**: Matches any whitespace character (space, tab, newline).
- **`\S`**: Matches any non-whitespace character.

--- 

## Quantifiers

Quantifiers specify how many times a character, group, or character class must be present in the input for a match to be found.

- **`{n}`**: Matches the preceding item exactly `n` times.
  - `\d{4}` matches exactly four digits.

- **`{n,}`**: Matches the preceding item `n` or more times.
  - `\d{2,}` matches two or more digits.

- **`{n,m}`**: Matches the preceding item at least `n` times, but not more than `m` times.
  - `\w{3,5}` matches any word with 3, 4, or 5 characters.

### Greedy vs. Lazy Matching

By default, quantifiers are *greedy*. They try to match as much text as possible.

- **Pattern**: `<.*>`
- **Text**: `<h1>This is a heading</h1>`
- **Greedy Match**: `<h1>This is a heading</h1>`

To make a quantifier *lazy* (match as little text as possible), add a `?` after it.

- **Pattern**: `<.*?>`
- **Text**: `<h1>This is a heading</h1>`
- **Lazy Match 1**: `<h1>`
- **Lazy Match 2**: `</h1>`

--- 

## Capturing Groups and Backreferences

When you group a part of a pattern with parentheses `()`, you create a *capturing group*. The text matched by this group is stored and can be reused.

- **Backreference**: You can refer to the captured text later in the pattern with `\1`, `\2`, etc.

**Example: Finding repeated words**
- **Pattern**: `(\w+) \1`
- **Text**: `hello hello world`
- **Match**: `hello hello`
  - `(\w+)` matches and captures `hello` into group 1.
  - ` ` matches the space.
  - `\1` refers back to what was captured in group 1 (`hello`) and matches it.

This is extremely useful for substitution. In `sed`, you could swap two words:
```bash
# Swap "John Smith" to "Smith, John"
echo "John Smith" | sed 's/(\w+) (\w+)/\2, \1/'
# Output: Smith, John
```
