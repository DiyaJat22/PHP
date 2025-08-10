# **PHP Strings**

## Strings in PHP

A **string** is a sequence of characters, like words or sentences, and in PHP, strings are enclosed in either **double quotes (" ")** or **single quotes (' ')**.

---

### Basic String Syntax

You can write strings like this:

```php
php
CopyEdit
echo "Hello";
echo 'Hello';

```

Both will output the word **Hello**.

---

### Difference Between Double and Single Quotes

There is a major difference between double-quoted and single-quoted strings in PHP:

- **Double Quotes (" ")**
    - Process **special characters** (like `\n` for a new line).
    - Parse variables inside the string and replace them with their values.
- **Single Quotes (' ')**
    - Treat everything literally.
    - Variables inside single quotes are **not** parsed; they show as plain text.

---

### Examples of Double vs Single Quotes with Variables

```php
php
CopyEdit
$x = "John";

// Double quotes parse the variable $x and output its value
echo "Hello $x";   // Outputs: Hello John

// Single quotes treat $x as a literal string
echo 'Hello $x';   // Outputs: Hello $x

```

---

### Special Characters in Double Quotes

Double quotes allow special escape sequences like:

| Escape Sequence | Meaning |
| --- | --- |
| `\n` | New line |
| `\t` | Tab |
| `\\` | Backslash |
| `\"` | Double quote |

Example:

```php
php
CopyEdit
echo "Hello\nWorld!"; // Outputs Hello and World! on two separate lines

```

Single quotes **do not** process these escape sequences (except for `\'` and `\\`).

---

### Common String Functions in PHP

PHP provides many useful functions to work with strings. Here are some key ones:

### 1. `strlen()` — String Length

Returns the number of characters in a string.

```php
php
CopyEdit
echo strlen("Hello world!");  // Outputs: 12

```

---

### 2. `str_word_count()` — Word Count

Counts the number of words in a string.

```php
php
CopyEdit
echo str_word_count("Hello world!");  // Outputs: 2

```

---

### 3. `strpos()` — Find Position of Text in String

Searches for a substring inside a string and returns the **first position** (index) of the match. Returns `FALSE` if not found.

Note: The position index starts at 0.

```php
php
CopyEdit
echo strpos("Hello world!", "world");  // Outputs: 6

```

---

### Summary Table

| Feature | Double Quotes (" ") | Single Quotes (' ') |
| --- | --- | --- |
| Variable parsing | Yes | No |
| Escape sequences | Yes (e.g. `\n`, `\t`) | No (only `\'` and `\\` supported) |
| Performance | Slightly slower | Slightly faster |

---

### Exercise Example Explained

What will the following output be?

```php
php
CopyEdit
$x = 5;
echo 'The price is $x';

```

- Since single quotes do **not** parse variables, the output will be:

```
swift
CopyEdit
The price is $x

```

---

### More Examples

```php
php
CopyEdit
$name = "Diya";

// Using double quotes — variable will be replaced
echo "Hello, $name!";  // Outputs: Hello, Diya!

// Using single quotes — variable will not be replaced
echo 'Hello, $name!';  // Outputs: Hello, $name!

// Using escape sequences with double quotes
echo "Line 1\nLine 2"; // Outputs two lines

// Using escape sequences with single quotes
echo 'Line 1\nLine 2'; // Outputs: Line 1\nLine 2 (no new line)

```

---

If you want, I can explain or show examples for other string functions like `substr()`, `str_replace()`, or anything else!

Here’s an all-in-one PHP example demonstrating:

- Single and double quoted strings
- Variable parsing in strings
- Escape sequences
- String functions: `strlen()`, `str_word_count()`, `strpos()`
- Showing output differences and explanations

```php
php
CopyEdit
<?php
// Define a variable
$name = "Diya";

// Double quoted string - variables and special characters are parsed
echo "Hello, $name!\n";  // Outputs: Hello, Diya! (with a new line)

// Single quoted string - variables are NOT parsed, literal output
echo 'Hello, $name!\n';  // Outputs: Hello, $name!\n (no new line)

// Using escape characters in double quotes
echo "This is line 1.\nThis is line 2.\n\n";

// Using escape characters in single quotes (only \' and \\ work)
echo 'This is line 1.\nThis is line 2.\n\n';

// Using string functions on a sample string
$text = "Hello world! Welcome to PHP.";

// strlen() - length of string
echo "Length of string: " . strlen($text) . "\n";  // Outputs: 27

// str_word_count() - count number of words
echo "Number of words: " . str_word_count($text) . "\n";  // Outputs: 5

// strpos() - find position of 'world' in the string
$pos = strpos($text, "world");
if ($pos !== false) {
    echo "'world' found at position: $pos\n";  // Outputs: 6
} else {
    echo "'world' not found\n";
}

// Demonstrate output differences with variables inside strings
$x = 5;
echo "The price is $x\n";    // Outputs: The price is 5
echo 'The price is $x\n';    // Outputs: The price is $x\n
?>

```

---

### What this example shows:

- How **double quotes** parse variables (`$name`, `$x`) and special characters like `\n`.
- How **single quotes** print everything literally.
- Use of key string functions (`strlen`, `str_word_count`, `strpos`) with outputs.
- Basic condition checking for `strpos`.
