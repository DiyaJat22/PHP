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

### ✅ Summary

You can use **`if` statements** with:

- **Comparison operators** to compare values.
- **Logical operators** to combine multiple conditions.
- **Ternary operator** for compact conditional expressions.
