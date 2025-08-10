# **while  Loop**

## 🔁 `while` Loop in PHP

### ✅ **Definition (Theory):**

A `while` loop in PHP executes a block of code **as long as a specified condition is true**. It checks the condition **before** each iteration.

---

### ✅ **Syntax:**

```php
while (condition) {
    // Code to be executed
}

```

- The loop will continue to run **until the condition becomes false**.
- If the condition is false at the beginning, the code block **won't run at all**.

---

### ✅ **Basic Example:**

```php
<?php
$i = 1;
while ($i <= 5) {
    echo "Number: $i <br>";
    $i++; // Increment to avoid infinite loop
}
?>

```

**Output:**

```
Number: 1
Number: 2
Number: 3
Number: 4
Number: 5

```

---

### ✅ **Real-Life Example: Even Numbers Between 1 to 10**

```php
<?php
$num = 1;
while ($num <= 10) {
    if ($num % 2 == 0) {
        echo "$num is even<br>";
    }
    $num++;
}
?>

```

---

### ✅ **Example: Using `break` inside a while loop**

```php
<?php
$x = 1;
while ($x <= 10) {
    if ($x == 4) {
        break; // Stop the loop when x is 4
    }
    echo "$x <br>";
    $x++;
}
?>

```

**Output:**

```
1
2
3

```

---

### ✅ **Example: Using `continue` in a while loop**

```php
<?php
$x = 0;
while ($x < 5) {
    $x++;
    if ($x == 3) {
        continue; // Skip 3
    }
    echo "$x <br>";
}
?>

```

**Output:**

```
1
2
4
5

```

---

### ⚠️ **Important Notes:**

- Be careful to update the condition variable (`$i++`) inside the loop. If not, the loop may run **forever**.
- Useful when you don’t know beforehand how many times you need to loop.

## ✅ **Example 1: Count from 1 to 5**

```php
<?php
$i = 1;
while ($i <= 5) {
    echo "Count: $i <br>";
    $i++;
}
?>

```

**Output:**

```
Count: 1
Count: 2
Count: 3
Count: 4
Count: 5

```

---

## ✅ **Example 2: Print Even Numbers from 1 to 10**

```php
<?php
$num = 1;
while ($num <= 10) {
    if ($num % 2 == 0) {
        echo "$num is even <br>";
    }
    $num++;
}
?>

```

**Output:**

```
2 is even
4 is even
6 is even
8 is even
10 is even

```

---

## ✅ **Example 3: Display Multiplication Table of 3**

```php
<?php
$i = 1;
while ($i <= 10) {
    echo "3 x $i = " . (3 * $i) . "<br>";
    $i++;
}
?>

```

**Output:**

```
3 x 1 = 3
3 x 2 = 6
3 x 3 = 9
...
3 x 10 = 30

```

---

## ✅ **Example 4: Countdown from 5 to 1**

```php
<?php
$i = 5;
while ($i >= 1) {
    echo "Countdown: $i <br>";
    $i--;
}
?>

```

**Output:**

```
Countdown: 5
Countdown: 4
Countdown: 3
Countdown: 2
Countdown: 1

```

---

## ✅ **Example 5: Stop Loop Using `break`**

```php
<?php
$i = 1;
while ($i <= 10) {
    if ($i == 6) {
        break; // Stop at 6
    }
    echo "$i <br>";
    $i++;
}
?>

```

**Output:**

```
1
2
3
4
5

```

---

## ✅ **Example 6: Skip a Number Using `continue`**

```php
<?php
$i = 0;
while ($i < 5) {
    $i++;
    if ($i == 3) {
        continue; // Skip 3
    }
    echo "$i <br>";
}
?>

```

**Output:**

```
1
2
4
5
```
