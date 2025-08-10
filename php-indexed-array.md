# Indexed Arrays in PHP

## ✅ Indexed Arrays in PHP

An indexed array in PHP is an array where each element is stored with a numeric index, starting from 0
by default.

# 🔹 How to Create Indexed Arrays

## 1. Using array() function:
 
```php
<?php
$colors = array("Red", "Green", "Blue");
?>
```
​
## 2. Using short array syntax [] (Recommended):

```php
<?php
$colors = ["Red", "Green", "Blue"];
?>
```
​
## 🔹 Accessing Elements

You can access elements using their index:

```
<?php
echo $colors[0];  // Output: Red
echo $colors[1];  // Output: Green
echo $colors[2];  // Output: Blue
?>
```
​
## 🔹 Looping Through Indexed Arrays

### Using for loop:

```php
<?php
$fruits = ["Apple", "Banana", "Cherry"];
$length = count($fruits);

for ($i = 0; $i < $length; $i++) {
    echo $fruits[$i] . "<br>";
}
?>
```
​
### Using foreach loop:
 
```php
<?php
$fruits = ["Apple", "Banana", "Cherry"];

foreach ($fruits as $fruit) {
    echo $fruit . "<br>";
}
?>
```
​
## ✅ Example: Storing and Displaying Student Names

```php
<?php
$students = ["Diya", "Riya", "Aarav"];

foreach ($students as $index => $name) {
    echo "Student $index: $name<br>";
}
?>
```
​
Output:

```
Student 0: Diya
Student 1: Riya
Student 2: Aarav
```
​
### 🧠 Key Points:

Indexed arrays use numeric keys.
Indexes start from 0 by default.
Use count() to get array length.
Use foreachor for loop to iterate.

## ✅ Example 1: Basic Indexed Array

```
<?php
$colors = ["Red", "Green", "Blue"];
echo $colors[0]; // Output: Red
echo "<br>";
echo $colors[1]; // Output: Green
echo "<br>";
echo $colors[2]; // Output: Blue
?>
```
​
## ✅ Example 2: Indexed Array Using for
 Loop

```php
<?php
$subjects = ["Math", "Science", "History", "English"];

for ($i = 0; $i < count($subjects); $i++) {
    echo "Subject $i: " . $subjects[$i] . "<br>";
}
?>
```
​
Output:

```
Subject 0: Math
Subject 1: Science
Subject 2: History
Subject 3: English
```
​
## ✅ Example 3: Using foreach
 Loop

```php
<?php
$fruits = ["Apple", "Banana", "Mango"];

foreach ($fruits as $fruit) {
    echo $fruit . "<br>";
}
?>
```
​
## ✅ Example 4: Manually Setting Indexes

```php
<?php
$numbers = array(0 => 100, 2 => 200, 5 => 500);

echo $numbers[0]; // 100
echo "<br>";
echo $numbers[2]; // 200
echo "<br>";
echo $numbers[5]; // 500
?>
```
​
## ✅ Example 5: Dynamic Array Using [] 
to Add Values

```php
<?php
$books = [];
$books[] = "PHP";
$books[] = "MySQL";
$books[] = "Linux";

foreach ($books as $book) {
    echo "Book: $book<br>";
}
?>
```
​
## ✅ Example 6: Array of Marks

```php
<?php
$marks = [85, 90, 78, 92];

$total = 0;
foreach ($marks as $mark) {
    $total += $mark;
}

$average = $total / count($marks);
echo "Total Marks: $total<br>";
echo "Average: $average";
?>
```
​
Output:

```
Total Marks: 345
Average: 86.25
```


