# PHP Comments

# PHP Comments

---

**Comments** in PHP are lines ignored by the PHP engine during execution. They do not affect the output or behavior of the program. Their main purpose is to help humans read and understand the code.

---

### Why Use Comments?

- Help others understand your code by explaining what it does.
- Remind yourself about your logic when you revisit the code later.
- Temporarily disable parts of the code without deleting them.

---

# Types of PHP Comments

---

### 1. Single-line Comments

Start with `//` or `#`.

Everything after these on the same line is ignored.

### Example:

```php
php
CopyEdit
<?php
// This is a single-line comment
echo "Welcome Home!";  // Outputs a welcome message

# This is also a single-line comment
?>

```

---

### 2. Multi-line Comments

Start with `/*` and end with `*/`.

They can span multiple lines.

Everything inside is ignored.

### Example:

```php
php
CopyEdit
<?php
/*
This is a multi-line comment.
It can cover more than one line.
*/
echo "Welcome Home!";
?>

```

---

# Using Comments to Ignore Code

---

### Single-line comment to disable code:

```php
php
CopyEdit
<?php
// echo "Welcome Home!";  // This line will NOT execute
echo "This line will execute.";
?>

```

Output:

```
pgsql
CopyEdit
This line will execute.

```

---

### Multi-line comment to disable multiple lines:

```php
php
CopyEdit
<?php
/*
echo "Welcome to my home!";
echo "Mi casa su casa!";
*/
echo "Hello!";
?>

```

Output:

```
CopyEdit
Hello!

```

---

# Comments Inside Code Lines

---

Multi-line comments can be used inside a line to disable part of it.

### Example:

```php
php
CopyEdit
<?php
$x = 5 /* + 15 */ + 5;
echo $x;
?>

```

**Explanation:**

The part `+ 15` is commented out, so the calculation becomes `5 + 5`, outputting:

```
CopyEdit
10

```

---

# Summary Table

| Comment Type       | Syntax               | Description                         | Example                             |
|--------------------|----------------------|-----------------------------------|-----------------------------------|
| Single-line comment | `// comment`         | Comments a single line            | `// This is a single-line comment` |
| Single-line comment | `# comment`          | Alternative single-line comment   | `# This is another single-line comment` |
| Multi-line comment  | `/* comment */`      | Comments multiple lines or blocks | `/* This is a multi-line comment spanning multiple lines */` |
