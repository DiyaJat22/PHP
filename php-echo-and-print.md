# **PHP echo and print Statements**

## PHP echo and print Statements

In PHP, **`echo`** and **`print`** are two language constructs used to output data (like text or variables) to the screen. They are very similar, but with some subtle differences.

---

### Differences Between `echo` and `print`

| Feature | `echo` | `print` |
| --- | --- | --- |
| Return value | No return value | Returns 1 (can be used in expressions) |
| Number of arguments | Can take multiple parameters | Can take only one argument |
| Speed | Slightly faster | Slightly slower |
| Usage | More commonly used | Less commonly used |

---

### The `echo` Statement

- `echo` is a language construct (not a function), so parentheses are optional.
- It can output one or more strings separated by commas.
- Can be used with both **double quotes** (supports variable parsing) and **single quotes** (variables won’t parse).

### Examples of `echo`:

```php
php
CopyEdit
<?php
echo "Hello";           // Without parentheses
echo("Hello");          // With parentheses

// Output text with HTML markup
echo "<h2>PHP is Fun!</h2>";
echo "Hello world!<br>";
echo "I'm about to learn PHP!<br>";

// Output multiple parameters (strings)
echo "This ", "string ", "was ", "made ", "with multiple parameters.";

// Output variables with double quotes (variables parsed)
$txt1 = "Learn PHP";
$txt2 = "W3Schools.com";
echo "<h2>$txt1</h2>";
echo "<p>Study PHP at $txt2</p>";

// Using single quotes (variables NOT parsed, so concatenate with . operator)
echo '<h2>' . $txt1 . '</h2>';
echo '<p>Study PHP at ' . $txt2 . '</p>';
?>

```

---

### The `print` Statement

- Like `echo`, `print` is a language construct and parentheses are optional.
- Can only take **one argument** (one string or variable).
- Returns a value of `1`, which means it can be used in expressions.

### Examples of `print`:

```php
php
CopyEdit
<?php
print "Hello";          // Without parentheses
print("Hello");         // With parentheses

// Output text with HTML markup
print "<h2>PHP is Fun!</h2>";
print "Hello world!<br>";
print "I'm about to learn PHP!";

// Output variables with double quotes (variables parsed)
$txt1 = "Learn PHP";
$txt2 = "W3Schools.com";
print "<h2>$txt1</h2>";
print "<p>Study PHP at $txt2</p>";

// Using single quotes (variables NOT parsed, concatenate with . operator)
print '<h2>' . $txt1 . '</h2>';
print '<p>Study PHP at ' . $txt2 . '</p>';
?>

```

---

### Summary

| Feature | `echo` | `print` |
| --- | --- | --- |
| Can output multiple strings? | Yes, separated by commas | No, only one argument |
| Returns a value? | No | Yes, returns 1 |
| Speed | Slightly faster | Slightly slower |
| Parentheses optional? | Yes | Yes |
| Use in expressions? | No | Yes |

---

### When to Use `echo` or `print`

- Use **`echo`** when you want to output one or more strings and don't need a return value. It's slightly faster and more flexible.
- Use **`print`** if you need a return value (for example, in expressions) or prefer its syntax.
