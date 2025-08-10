# Creating Arrays in PHP

### ✅ Creating Arrays in PHP

In PHP, you can create **three main types** of arrays:

1. **Indexed Arrays** – with numeric keys
2. **Associative Arrays** – with named keys
3. **Multidimensional Arrays** – arrays inside arrays

---

## 🔹 1. Indexed Array (Numeric Keys)

### Syntax:

```php
<?php
// Using array() function
$colors = array("Red", "Green", "Blue");

// Using short array syntax (recommended)
$fruits = ["Apple", "Banana", "Mango"];
?>

```

### Accessing:

```php
echo $colors[0]; // Red

```

---

## 🔹 2. Associative Array (Named Keys)

### Syntax:

```php
<?php
// Using named keys
$person = array("name" => "Diya", "age" => 22);

// Short array syntax
$student = ["roll" => 101, "class" => "12th"];
?>

```

### Accessing:

```php
echo $person["name"]; // Diya

```

---

## 🔹 3. Multidimensional Array (Array within Array)

### Syntax:

```php
<?php
$students = [
    ["name" => "Diya", "marks" => 85],
    ["name" => "Riya", "marks" => 90],
    ["name" => "Aarav", "marks" => 88]
];

echo $students[1]["name"]; // Riya
?>

```

---

## 🔹 Example: Creating and Printing All Three Types

```php
<?php
// Indexed
$colors = ["Red", "Blue", "Green"];

// Associative
$user = ["username" => "diya", "email" => "diya@example.com"];

// Multidimensional
$marks = [
    "Diya" => ["Math" => 90, "English" => 85],
    "Aarav" => ["Math" => 88, "English" => 80]
];

echo $colors[1] . "<br>";                 // Blue
echo $user["email"] . "<br>";            // diya@example.com
echo $marks["Diya"]["Math"];             // 90
?>
```
