# PHP `if...else`

## ✅ What is `if...else` in PHP?

The `if...else` statement allows you to **execute one block of code if a condition is true**, and another block **if the condition is false**.

---

## 🔹 Syntax:

```php
if (condition) {
    // code to run if condition is true
} else {
    // code to run if condition is false
}

```

---

## ✅ Example 1: Age Check

```php
<?php
$age = 17;

if ($age >= 18) {
    echo "You are an adult.";
} else {
    echo "You are a minor.";
}
?>

```

**Output:**

```
You are a minor.

```

---

## ✅ Example 2: Even or Odd Number

```php
<?php
$num = 9;

if ($num % 2 == 0) {
    echo "$num is even.";
} else {
    echo "$num is odd.";
}
?>

```

**Output:**

```
9 is odd.

```

---

## ✅ Example 3: Password Check

```php
<?php
$password = "admin123";

if ($password == "admin123") {
    echo "Access granted.";
} else {
    echo "Access denied.";
}
?>

```

**Output:**

```
Access granted.

```

---

## ✅ Example 4: Login System

```php
<?php
$username = "diya";
$enteredName = "diya";

if ($enteredName == $username) {
    echo "Welcome, $username!";
} else {
    echo "Username not recognized.";
}
?>

```

---

## 🧠 Key Points

- `if...else` checks **one condition** and gives **two possible outcomes**.
- It is the simplest form of conditional branching in PHP.
- The `else` block is **optional**.

---

## ✅ Real-World Use Example: Form Submission

```php
<?php
$submitted = true;

if ($submitted) {
    echo "Form submitted successfully.";
} else {
    echo "Please fill out the form.";
}
?>
```
