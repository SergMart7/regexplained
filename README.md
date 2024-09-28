
# Understanding Regex for Email Validation

Regular expressions, or regex, are powerful tools used to search and validate strings that follow specific patterns. They may look intimidating at first, but they break down into smaller components that can be easy to understand. In this tutorial, we will explore how a regex pattern can validate email addresses, step by step.

## Summary

We are going to explain the following regex, which checks if a string is a valid email address:

```
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
```

In simple terms, this regex makes sure that an email address has characters before and after the `@`, and ends with a valid domain extension (like `.com` or `.net`).

## Table of Contents

- [What is Regex?](#what-is-regex)
- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)
- [Examples](#examples)
- [Common Mistakes](#common-mistakes)

## What is Regex?

A regex is like a search pattern. Think of it as a checklist for what you want to find in a string. In our case, we are looking for a pattern that matches a typical email address format.

## Regex Components

### Anchors

Anchors are used to specify where the pattern starts and ends.

- `^`: This is called the "caret" symbol. It makes sure that the pattern matches from the **start** of the string.
- `$`: This is the dollar sign, which makes sure that the pattern matches up to the **end** of the string.

**Example**: `^abc$` would only match the string "abc" exactly, with nothing before or after it.

### Quantifiers

Quantifiers tell regex how many times a certain character, group, or character class should appear.

- `+`: Means "one or more times." For example, `[a-z]+` means "match at least one letter."
- `{2,6}`: Means "between 2 and 6 times." For example, `[0-9]{2,6}` would match any number that is 2 to 6 digits long (like `12`, `123`, `123456`).

In our regex:
- `[a-z0-9_\.-]+` uses `+` to ensure that the email address has one or more valid characters before the `@`.
- `[a-z\.]{2,6}` uses `{2,6}` to make sure the domain extension is between 2 and 6 characters long (like `.com` or `.org`).

### Grouping Constructs

Grouping constructs help you group parts of a regex together and capture them for use.

- `()` is used to group parts of the regex into "capturing groups."
- Each group is like a mini-pattern within the main regex.

In our regex:
- `([a-z0-9_\.-]+)` captures the part of the email address before the `@`.
- `([\da-z\.-]+)` captures the domain name (like `gmail` or `yahoo`).
- `([a-z\.]{2,6})` captures the domain extension (like `com`, `net`, `org`).

### Bracket Expressions

Bracket expressions are used to find a range of characters.

- `[a-z0-9]`: Matches any lowercase letter or digit.
- `[\d]`: Matches any digit, from 0 to 9.
- `[a-z\.]{2,6}`: Matches any lowercase letter or a dot (period) between 2 and 6 times.

### Character Classes

Character classes let you match different types of characters.

- `\d`: Matches any digit (same as `[0-9]`).
- `\w`: Matches any "word character" (letters, digits, and underscores).

### The OR Operator

The OR operator (`|`) allows you to match one thing or another. However, our email regex does not use the OR operator. An example of how it works:
- `cat|dog`: Matches either "cat" or "dog."

### Flags

Flags modify how the regex is processed. They go after the last slash (`/`). Here are a few examples:
- `g`: Global search (finds all matches, not just the first).
- `i`: Case-insensitive search (ignores lowercase/uppercase).

Our regex does not use any flags.

### Character Escapes

Escapes are used to match characters that have special meanings in regex.

- `\.`: A dot `.` normally matches any character, but `\.` makes it match a literal period.
  
In our regex, `\.` makes sure that the period in the domain (like `gmail.com`) is treated as a period and not as a wildcard character.

## Examples

Let’s break down some valid and invalid examples based on our regex:

- **Valid Examples**:
  - `example.email@domain.com`: This has characters before and after the `@` and ends with `.com`.
  - `user_123@sub-domain.co.uk`: This is valid because underscores, digits, and hyphens are allowed.

- **Invalid Examples**:
  - `plainaddress`: Missing the `@` and domain.
  - `@missingusername.com`: No characters before the `@`.
  - `username@.com`: Domain is missing before the `.`.

## Common Mistakes

1. **Missing Anchors**: Not using `^` and `$` can lead to partial matches.
   - Example: Without these anchors, the regex might match only part of a string.

2. **Incorrect Quantifiers**: Using `*` instead of `+` may allow empty strings to match.

3. **Forgetting Escapes**: Not escaping special characters like `.` can lead to unintended matches.

## Author

This brief tutorial and regex explanation was written by Sergio Martinez, an upcoming developer with a huge passion for creating new thigs and also learning new things. I enjoy sharing my creations and knowledge with others, as well as to recieve any feedback.
Huh? Want to see more? go ahead and check out my [Github](https://github.com/Sergmart7).