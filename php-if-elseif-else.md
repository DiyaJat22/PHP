# PHP if...elseif...else

## ✅ What is `if...elseif...else` in PHP?

This structure allows you to **check multiple conditions in sequence**.

- The `if` condition is checked first.
- If it’s false, PHP checks the `elseif` conditions (in order).
- If none of them are true, it executes the `else` block.

---

## 🔹 Syntax:

```php
if (condition1) {
    // Code if condition1 is true
} elseif (condition2) {
    // Code if condition2 is true
} elseif (condition3) {
    // Code if condition3 is true
} else {
    // Code if none of the above conditions are true
}

```

---

## ✅ Example 1: Grading System

```php
<?php
$marks = 82;

if ($marks >= 90) {
    echo "Grade: A";
} elseif ($marks >= 75) {
    echo "Grade: B";
} elseif ($marks >= 60) {
    echo "Grade: C";
} elseif ($marks >= 33) {
    echo "Grade: D";
} else {
    echo "Fail";
}
?>

```

**Output:**

```
Grade: B

```

---

## ✅ Example 2: Temperature Check

```php
<?php
$temp = 30;

if ($temp >= 40) {
    echo "Very Hot";
} elseif ($temp >= 30) {
    echo "Hot";
} elseif ($temp >= 20) {
    echo "Warm";
} else {
    echo "Cold";
}
?>

```

**Output:**

```
Hot

```

---

## ✅ Example 3: Login with Role Check

```php
<?php
$role = "editor";

if ($role == "admin") {
    echo "Welcome Admin!";
} elseif ($role == "editor") {
    echo "Welcome Editor!";
} elseif ($role == "user") {
    echo "Welcome User!";
} else {
    echo "Access Denied.";
}
?>

```

**Output:**

```
Welcome Editor!

```

---

## 🧠 Key Points

- Use **`if...elseif...else`** when you have more than two choices to evaluate.
- Conditions are checked **in order** from top to bottom.
- Once one is true, the rest are skipped.

### ✅ Example 1: Student Grade Checker

```php
<?php
$score = 68;

if ($score >= 90) {
    echo "Grade: A+";
} elseif ($score >= 75) {
    echo "Grade: A";
} elseif ($score >= 60) {
    echo "Grade: B";
} elseif ($score >= 45) {
    echo "Grade: C";
} elseif ($score >= 33) {
    echo "Grade: D";
} else {
    echo "Grade: F (Fail)";
}
?>

```

**Output:**

```
Grade: B

```

---

### ✅ Example 2: Time of Day Greeting

```php
<?php
$hour = 14;

if ($hour < 12) {
    echo "Good Morning!";
} elseif ($hour < 17) {
    echo "Good Afternoon!";
} elseif ($hour < 21) {
    echo "Good Evening!";
} else {
    echo "Good Night!";
}
?>

```

**Output:**

```
Good Afternoon!

```

---

### ✅ Example 3: Ticket Pricing Based on Age

```php
<?php
$age = 65;

if ($age < 5) {
    echo "Ticket is Free.";
} elseif ($age <= 18) {
    echo "Ticket Price: ₹50";
} elseif ($age < 60) {
    echo "Ticket Price: ₹100";
} else {
    echo "Ticket Price: ₹70 (Senior Citizen Discount)";
}
?>

```

**Output:**

```
Ticket Price: ₹70 (Senior Citizen Discount)

```

---

### ✅ Example 4: User Access Role

```php
<?php
$role = "moderator";

if ($role == "admin") {
    echo "Full Access";
} elseif ($role == "moderator") {
    echo "Limited Access";
} elseif ($role == "user") {
    echo "Basic Access";
} else {
    echo "No Access";
}
?>

```

**Output:**

```
Limited Access

```

---

### ✅ Example 5: Simple Calculator

```php
<?php
$a = 10;
$b = 5;
$operation = "multiply";

if ($operation == "add") {
    echo $a + $b;
} elseif ($operation == "subtract") {
    echo $a - $b;
} elseif ($operation == "multiply") {
    echo $a * $b;
} elseif ($operation == "divide") {
    echo $a / $b;
} else {
    echo "Invalid operation!";
}
?>

```

**Output:**

```
50
```
