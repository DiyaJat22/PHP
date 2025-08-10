# `for` Loop

## 🔁 `for` Loop in PHP

### ✅ **Definition (Theory):**

A `for` loop is used when you **know in advance** how many times you want to execute a block of code.

---

### ✅ **Syntax:**

```php
for (initialization; condition; increment/decrement) {
    // Code to be executed
}

```

- **Initialization**: Set a counter (e.g., `$i = 0`)
- **Condition**: The loop runs **while** this is `true`
- **Increment/Decrement**: Changes the counter after each loop

---

## 📘 **Examples**

---

### 🔹 **Example 1: Count from 1 to 5**

```php
<?php
for ($i = 1; $i <= 5; $i++) {
    echo "Count: $i <br>";
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

### 🔹 **Example 2: Print Even Numbers Between 1 to 10**

```php
<?php
for ($i = 1; $i <= 10; $i++) {
    if ($i % 2 == 0) {
        echo "$i is even<br>";
    }
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

### 🔹 **Example 3: Reverse Loop (Countdown)**

```php
<?php
for ($i = 5; $i >= 1; $i--) {
    echo "Countdown: $i <br>";
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

### 🔹 **Example 4: Multiplication Table of 6**

```php
<?php
for ($i = 1; $i <= 10; $i++) {
    echo "6 x $i = " . (6 * $i) . "<br>";
}
?>

```

**Output:**

```
6 x 1 = 6
6 x 2 = 12
...
6 x 10 = 60

```

---

### 🔹 **Example 5: Using `break` and `continue`**

```php
<?php
for ($i = 1; $i <= 10; $i++) {
    if ($i == 4) {
        continue; // skip 4
    }
    if ($i == 8) {
        break; // stop at 8
    }
    echo "$i <br>";
}
?>

```

**Output:**

```
1
2
3
5
6
7

```

---

## 📝 When to Use `for` Loop

- You know the **exact number of iterations**.
- Looping through numbers, indexes, or table rows.
- Generating patterns, multiplication tables, etc.
