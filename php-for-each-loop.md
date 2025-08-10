# **foreach Loop**

## 🔁 `foreach` Loop in PHP

### ✅ **Definition (Theory):**

The `foreach` loop is used to iterate **over arrays**. It loops through each **key-value pair** or just the **values** in an array.

---

### ✅ **Syntax:**

```php
foreach ($array as $value) {
    // Code to execute
}

```

```php
foreach ($array as $key => $value) {
    // Code to execute
}

```

---

## 📘 **Examples**

---

### 🔹 **Example 1: Simple Indexed Array**

```php
<?php
$fruits = ["Apple", "Banana", "Mango", "Orange"];

foreach ($fruits as $fruit) {
    echo "$fruit <br>";
}
?>

```

**Output:**

```
Apple
Banana
Mango
Orange

```

---

### 🔹 **Example 2: Associative Array (With Key and Value)**

```php
<?php
$person = [
    "name" => "Diya",
    "age" => 22,
    "course" => "Cyber Security"
];

foreach ($person as $key => $value) {
    echo "$key: $value <br>";
}
?>

```

**Output:**

```
name: Diya
age: 22
course: Cyber Security

```

---

### 🔹 **Example 3: Display Student Marks**

```php
<?php
$marks = [
    "Math" => 90,
    "English" => 85,
    "Science" => 92
];

foreach ($marks as $subject => $score) {
    echo "Subject: $subject, Score: $score <br>";
}
?>

```

**Output:**

```
Subject: Math, Score: 90
Subject: English, Score: 85
Subject: Science, Score: 92

```

---

### 🔹 **Example 4: Nested Array (Loop Inside Loop)**

```php
<?php
$students = [
    "Diya" => ["Math" => 90, "English" => 85],
    "Amit" => ["Math" => 78, "English" => 88]
];

foreach ($students as $name => $subjects) {
    echo "<strong>$name's Marks:</strong><br>";
    foreach ($subjects as $subject => $mark) {
        echo "$subject: $mark <br>";
    }
    echo "<br>";
}
?>

```

---

## ✅ When to Use `foreach`:

- Looping through arrays (indexed or associative).
- Reading values from form submissions stored in arrays.
- Easier and cleaner than `for` loop for arrays.
