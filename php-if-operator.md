# PHP if Operators

## ✅ Types of Operators Used in `if` Conditions

### 1. **Comparison Operators**

| Operator | Meaning | Example |
| --- | --- | --- |
| `==` | Equal to | `$x == $y` |
| `===` | Identical (value + type) | `$x === $y` |
| `!=` | Not equal to | `$x != $y` |
| `!==` | Not identical | `$x !== $y` |
| `>` | Greater than | `$x > $y` |
| `<` | Less than | `$x < $y` |
| `>=` | Greater than or equal to | `$x >= $y` |
| `<=` | Less than or equal to | `$x <= $y` |

---

### ✅ Example Using Comparison Operators

```php
<?php
$score = 75;

if ($score >= 50) {
    echo "You passed!";
} else {
    echo "You failed!";
}
?>

```

---

### 2. **Logical Operators**

| Operator | Description | Example |
| --- | --- | --- |
| `&&` | AND – both conditions must be true | `$x > 10 && $x < 20` |
| ` |  | ` |
| `!` | NOT – reverses the condition’s result | `!($x == 10)` |

---

### ✅ Example Using Logical Operators

```php
<?php
$age = 20;
$citizen = true;

if ($age >= 18 && $citizen) {
    echo "Eligible to vote.";
} else {
    echo "Not eligible.";
}
?>

```

---

### 3. **Ternary Operator (Short `if...else`)**

```php
<?php
$marks = 40;
echo ($marks >= 33) ? "Pass" : "Fail";
?>

```

---

## ✅ What is `if` in PHP?

The `if` statement is used to **execute code only if a certain condition is true**.

### 🔹 Basic Syntax:

```php
if (condition) {
    // code to execute if condition is true
}

```

---

## ✅ Example 1: Basic `if` Statement

```php
<?php
$age = 18;

if ($age >= 18) {
    echo "You are eligible to vote.";
}
?>

```

**Output:**

```
You are eligible to vote.

```

---

## ✅ Example 2: `if...else` Statement

```php
<?php
$age = 16;

if ($age >= 18) {
    echo "You can vote.";
} else {
    echo "You are too young to vote.";
}
?>

```

**Output:**

```
You are too young to vote.

```

---

## ✅ Example 3: `if...elseif...else` Statement

This is useful when checking multiple conditions.

```php
<?php
$score = 85;

if ($score >= 90) {
    echo "Grade: A";
} elseif ($score >= 75) {
    echo "Grade: B";
} elseif ($score >= 60) {
    echo "Grade: C";
} else {
    echo "Grade: F";
}
?>

```

**Output:**

```
Grade: B

```

---

## ✅ Example 4: Using Logical Operators with `if`

```php
<?php
$username = "diya";
$password = "secure123";

if ($username == "diya" && $password == "secure123") {
    echo "Login successful!";
} else {
    echo "Invalid login.";
}
?>

```

---

## ✅ Example 5: Nested `if` Statements

```php
php
CopyEdit
<?php
$marks = 80;
$attendance = 90;

if ($marks >= 75) {
    if ($attendance >= 80) {
        echo "Eligible for scholarship.";
    } else {
        echo "Good marks, but attendance too low.";
    }
}
?>
```

### ✅ Summary

You can use **`if` statements** with:

- **Comparison operators** to compare values.
- **Logical operators** to combine multiple conditions.
- **Ternary operator** for compact conditional expressions.
