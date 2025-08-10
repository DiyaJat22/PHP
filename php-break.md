# break

## 🛑 `break` Statement in PHP

### ✅ **Definition (Theory):**

The `break` statement is used to **terminate the execution of a loop** (like `for`, `while`, `do...while`, or `foreach`) **immediately** when a certain condition is met.

It stops the loop and **continues with the code after the loop**.

---

### ✅ **Syntax:**

```php
break;

```

---

## 📘 **Examples**

---

### 🔹 **Example 1: `break` in a `for` loop**

```php
<?php
for ($i = 1; $i <= 10; $i++) {
    if ($i == 5) {
        break;
    }
    echo "Number: $i <br>";
}
?>

```

**Output:**

```
Number: 1
Number: 2
Number: 3
Number: 4

```

📝 *When `$i` is 5, the loop stops.*

---

### 🔹 **Example 2: `break` in a `while` loop**

```php
<?php
$x = 1;
while ($x <= 10) {
    if ($x == 4) {
        break;
    }
    echo "x = $x <br>";
    $x++;
}
?>

```

**Output:**

```
x = 1
x = 2
x = 3

```

---

### 🔹 **Example 3: `break` in a `foreach` loop**

```php
<?php
$colors = ["Red", "Green", "Blue", "Yellow"];

foreach ($colors as $color) {
    if ($color == "Blue") {
        break;
    }
    echo "$color <br>";
}
?>

```

**Output:**

```
Red
Green

```

---

### 🔹 **Example 4: Use in `switch` Statement**

```php
<?php
$day = "Tuesday";

switch ($day) {
    case "Monday":
        echo "Start of the week";
        break;
    case "Tuesday":
        echo "Second day of the week";
        break;
    default:
        echo "Some other day";
}
?>

```

**Output:**

```
Second day of the week

```

✅ `break` is **required in switch-case** to prevent fall-through.
