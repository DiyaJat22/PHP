# PHP Regular Expressions (Regex)

### ✅ PHP Regular Expressions (Regex) – Explained with Examples

**Regular Expressions (regex)** in PHP are patterns used to match strings. They’re useful for:

- Validating inputs (like emails, phone numbers)
- Searching and replacing text
- Extracting specific data

---

### 🔹 PHP Regex Functions

| Function | Description |
| --- | --- |
| `preg_match()` | Checks if a pattern matches a string |
| `preg_match_all()` | Finds all matches of a pattern |
| `preg_replace()` | Replaces pattern matches |
| `preg_split()` | Splits a string by a pattern |

---

### ✅ 1. `preg_match()` – Match a pattern

```php
<?php
$pattern = "/diya/i";  // 'i' means case-insensitive
$text = "Hello Diya, welcome!";
if (preg_match($pattern, $text)) {
    echo "Match found!";
} else {
    echo "No match.";
}
?>

```

---

### ✅ 2. `preg_match_all()` – Find all matches

```php
<?php
$text = "Email me at test@example.com or contact@example.org";
preg_match_all("/[a-z0-9._%+-]+@[a-z0-9.-]+\.[a-z]{2,}/i", $text, $matches);
print_r($matches[0]);
?>

```

---

### ✅ 3. `preg_replace()` – Search & replace

```php
<?php
$text = "My phone number is 123-456-7890.";
$result = preg_replace("/[0-9]{3}-[0-9]{3}-[0-9]{4}/", "***-***-****", $text);
echo $result;
?>

```

---

### ✅ 4. `preg_split()` – Split a string by regex pattern

```php
php
CopyEdit
<?php
$text = "PHP,Python|Java C++";
$parts = preg_split("/[,| ]+/", $text);
print_r($parts);
?>

```

---

### 🔹 Useful Regex Patterns

| Pattern | Description | Example Match |
| --- | --- | --- |
| `/^[a-zA-Z]+$/` | Only letters | `Diya` |
| `/^[0-9]{10}$/` | Exactly 10 digits | `1234567890` |
| `/^\d+$/` | Only digits | `42` |
| `/^\w+@\w+\.\w+$/` | Simple email | `user@example.com` |
| `/https?:\/\/[^\s]+/` | URLs | `http://example.com` |

---

### 📌 Example: Validate Email Address

```php
<?php
$email = "diya@example.com";
if (preg_match("/^[\w.-]+@[\w.-]+\.[a-z]{2,6}$/i", $email)) {
    echo "Valid email.";
} else {
    echo "Invalid email.";
}
?>

```

## 🔸 Common Regex Symbols and Their Meaning

| Symbol | Meaning | Example | Matches |
| --- | --- | --- | --- |
| `.` | Any single character | `/.at/` | `cat`, `bat`, `hat` |
| `^` | Start of string | `/^Hi/` | `Hi there` |
| `$` | End of string | `/end$/` | `The end` |
| `\d` | Digit (0–9) | `/\d\d/` | `42` |
| `\w` | Word character (a-z, A-Z, 0-9, _) | `/\w+/` | `hello123` |
| `\s` | Whitespace | `/\s/` | Space, tab |
| `+` | One or more | `/a+/` | `a`, `aaa` |
| `*` | Zero or more | `/lo*/` | `l`, `loo` |
| `?` | Zero or one | `/colou?r/` | `color`, `colour` |
| `{n}` | Exactly n times | `/\d{3}/` | `123` |
| `[abc]` | a, b, or c | `/[abc]/` | `a`, `b`, `c` |
| `[^abc]` | Not a, b, or c | `/[^abc]/` | `d`, `e` |
| `(abc)` | Group | `/(ab)+/` | `abab` |

---

## 🔸 PHP Regex Functions

### 1. `preg_match()` – Match once

```php
<?php
$text = "My name is Diya.";
if (preg_match("/diya/i", $text)) {
    echo "Match found!";
} else {
    echo "Not found.";
}
?>

```

### 2. `preg_match_all()` – Match all instances

```php
<?php
$text = "diya@example.com, admin@example.org";
preg_match_all("/[a-z0-9._%+-]+@[a-z0-9.-]+\.[a-z]{2,}/i", $text, $matches);
print_r($matches[0]);  // Output: all emails found
?>

```

### 3. `preg_replace()` – Replace match

```php
<?php
$text = "123-456-7890";
echo preg_replace("/\d{3}-\d{3}-\d{4}/", "xxx-xxx-xxxx", $text);
?>

```

### 4. `preg_split()` – Split string by pattern

```php
<?php
$str = "apple, banana | mango orange";
$parts = preg_split("/[,| ]+/", $str);
print_r($parts);
?>

```

---

## 🔸 Example: Validate Email with Regex

```php
<?php
$email = "diya@example.com";
if (preg_match("/^[\w.-]+@[\w.-]+\.[a-z]{2,6}$/i", $email)) {
    echo "Valid email";
} else {
    echo "Invalid email";
}
?>

```

---

---

## 📘 Summary

| Function | Purpose |
| --- | --- |
| `preg_match()` | Check if a string matches a pattern |
| `preg_match_all()` | Find all matches in a string |
| `preg_replace()` | Replace matched text |
| `preg_split()` | Split text by regex |
