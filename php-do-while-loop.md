# `do...while` Loop

## 🔁 `do...while` Loop in PHP

### ✅ **Definition (Theory):**

The `do...while` loop executes a block of code **at least once**, and then **repeats** the loop **as long as the condition is true**.

---

### ✅ **Syntax:**

```php
do {
    // Code to execute
} while (condition);

```

- The code inside the `do` block **executes first**, then the condition is checked.
- Even if the condition is `false`, the code block will run **once**.

---

## 📘 **Examples**

---

### 🔹 **Example 1: Basic Usage**

```php
<?php
$x = 1;
do {
    echo "Value: $x <br>";
    $x++;
} while ($x <= 5);
?>

```

**Output:**

```
Value: 1
Value: 2
Value: 3
Value: 4
Value: 5

```

---

### 🔹 **Example 2: Condition False Initially**

```php
<?php
$x = 10;
do {
    echo "Executed once even though x > 5 <br>";
} while ($x < 5);
?>

```

**Output:**

```
Executed once even though x > 5

```

💡 *Even though the condition is false, the loop runs one time.*

---

### 🔹 **Example 3: Print Odd Numbers from 1 to 10**

```php
<?php
$number = 1;
do {
    if ($number % 2 != 0) {
        echo "$number is odd<br>";
    }
    $number++;
} while ($number <= 10);
?>

```

**Output:**

```
1 is odd
3 is odd
5 is odd
7 is odd
9 is odd

```

---

### 🔹 **Example 4: Multiplication Table (e.g., 7)**

```php
<?php
$i = 1;
do {
    echo "7 x $i = " . (7 * $i) . "<br>";
    $i++;
} while ($i <= 10);
?>

```

**Output:**

```
7 x 1 = 7
7 x 2 = 14
...
7 x 10 = 70

```

---

### 🔹 **Example 5: Use of `break` and `continue`**

```php
<?php
$i = 0;
do {
    $i++;
    if ($i == 4) {
        continue; // skip 4
    }
    if ($i == 7) {
        break; // stop at 7
    }
    echo "i = $i <br>";
} while ($i < 10);
?>

```

**Output:**

```
i = 1
i = 2
i = 3
i = 5
i = 6

```

---
