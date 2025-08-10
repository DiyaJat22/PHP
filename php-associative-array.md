# Associative Arrays in PHP

### ✅ Associative Arrays in PHP

An **associative array** uses **named keys** (instead of numeric indexes) to store and access values. It works like a dictionary in other programming languages.

---

## 🔹 Syntax

### Using `array()`:

```php
<?php
$person = array("name" => "Diya", "age" => 22, "city" => "Indore");
?>

```

### Using `[]` syntax (Recommended):

```php
<?php
$person = ["name" => "Diya", "age" => 22, "city" => "Indore"];
?>

```

---

## 🔹 Accessing Values

```php
<?php
echo $person["name"];  // Output: Diya
echo $person["age"];   // Output: 22
echo $person["city"];  // Output: Indore
?>

```

---

## 🔹 Looping Through Associative Arrays

### Using `foreach`:

```php
<?php
$person = ["name" => "Diya", "age" => 22, "city" => "Indore"];

foreach ($person as $key => $value) {
    echo "$key: $value<br>";
}
?>

```

---

## ✅ Examples

### Example 1: Student Information

```php
<?php
$student = [
    "name" => "Aarav",
    "roll" => 101,
    "class" => "12th"
];

echo "Name: " . $student["name"] . "<br>";
echo "Roll No: " . $student["roll"] . "<br>";
echo "Class: " . $student["class"];
?>

```

---

### Example 2: Product List

```php
<?php
$products = [
    "pen" => 10,
    "pencil" => 5,
    "eraser" => 3
];

foreach ($products as $item => $price) {
    echo "$item costs ₹$price<br>";
}
?>

```

---

### Example 3: Login Credentials

```php
<?php
$users = [
    "admin" => "admin123",
    "diya" => "secure@456",
    "guest" => "guest123"
];

echo "Password for diya: " . $users["diya"];
?>

```

---

## 🧠 Key Points:

- Associative arrays use **named keys**.
- Ideal for structured data (like user profiles, products, settings).
- Loop using `foreach ($array as $key => $value)`.

### ✅ Example 1: Basic Associative Array

```php
<?php
$person = [
    "name" => "Diya",
    "age" => 22,
    "city" => "Indore"
];

echo "Name: " . $person["name"] . "<br>";
echo "Age: " . $person["age"] . "<br>";
echo "City: " . $person["city"];
?>

```

**Output:**

```
Name: Diya
Age: 22
City: Indore

```

---

### ✅ Example 2: Associative Array with `foreach` Loop

```php
<?php
$car = [
    "brand" => "Toyota",
    "model" => "Innova",
    "year" => 2020
];

foreach ($car as $key => $value) {
    echo ucfirst($key) . ": $value<br>";
}
?>

```

**Output:**

```
Brand: Toyota
Model: Innova
Year: 2020

```

---

### ✅ Example 3: Storing and Showing Prices

```php
<?php
$products = [
    "Pen" => 10,
    "Notebook" => 50,
    "Bag" => 500
];

foreach ($products as $item => $price) {
    echo "$item = ₹$price<br>";
}
?>

```

---

### ✅ Example 4: Country and Capital

```php
<?php
$capitals = [
    "India" => "New Delhi",
    "USA" => "Washington, D.C.",
    "Japan" => "Tokyo"
];

echo "Capital of India is " . $capitals["India"];
?>

```

**Output:**

```
Capital of India is New Delhi

```

---

### ✅ Example 5: Login Page Simulation

```php
<?php
$users = [
    "admin" => "admin123",
    "diya" => "secure@456"
];

$username = "diya";
$password = "secure@456";

if ($users[$username] == $password) {
    echo "Login successful!";
} else {
    echo "Invalid credentials.";
}
?>

```

**Output:**

```
Login successful!

```

## ✅ Example 6: Student Marks

```php
<?php
$marks = [
    "Math" => 90,
    "Science" => 85,
    "English" => 88
];

$total = 0;
foreach ($marks as $subject => $mark) {
    echo "$subject: $mark<br>";
    $total += $mark;
}

$average = $total / count($marks);
echo "Average: $average";
?>
```




---


