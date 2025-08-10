# **$GLOBALS Superglobal**

## 🔍 What is `$GLOBALS`?

`$GLOBALS` is a **superglobal associative array** in PHP that stores **all global variables**. This means you can access any global variable from **anywhere in your script**, including inside functions or methods.

✅ It's especially useful when you want to use or modify a global variable **inside a function** without explicitly declaring it as `global`.

---

## 📌 Syntax

```php
$GLOBALS['variable_name']

```

---

## ✅ Example 1: Accessing Global Variable Inside a Function

```php
<?php
$x = 10;
$y = 20;

function addNumbers() {
    $GLOBALS['z'] = $GLOBALS['x'] + $GLOBALS['y'];
}

addNumbers();
echo "Sum: " . $z; // Output: Sum: 30
?>

```

🧠 What's Happening:

- `$x` and `$y` are **global variables**.
- Inside the `addNumbers()` function, we **access and use them via `$GLOBALS`**.
- We store the result in `$GLOBALS['z']`, making `$z` globally accessible.

---

## ✅ Example 2: Without `$GLOBALS` (for comparison)

```php
<?php
$a = 5;
$b = 7;

function multiply() {
    global $a, $b;
    $c = $a * $b;
    echo "Product: $c";
}

multiply(); // Output: Product: 35
?>

```

📌 Here, we used `global $a, $b;`, which is **another way** of accessing global variables — but `$GLOBALS` is often preferred in larger applications for **clarity and dynamic access**.

---

## ✅ Example 3: Using `$GLOBALS` Dynamically

```php
<?php
$varName = "username";
$GLOBALS[$varName] = "Diya";

echo "User: " . $username; // Output: User: Diya
?>

```

🧠 Here, we dynamically created a variable using `$GLOBALS` — very useful in configurations or frameworks.

---

## ✅ Example 4: Logging All Global Variables

```php
<?php
$name = "Diya";
$role = "Cyber Security";

echo "<pre>";
print_r($GLOBALS);
echo "</pre>";

```

🧾 This will print **all current global variables** in a readable format.

---

## ⚠️ When to Use `$GLOBALS`

| ✅ Use When | ❌ Avoid When |
| --- | --- |
| Accessing/modifying global vars in functions | Overusing global state (hard to debug) |
| Dynamic variable access | For passing data — use parameters |
| Simple scripts | In OOP-heavy or layered apps |

## ✅ **Example 1: Simple Arithmetic Using `$GLOBALS`**

```php
<?php
$a = 5;
$b = 10;

function add() {
    $GLOBALS['sum'] = $GLOBALS['a'] + $GLOBALS['b'];
}

add();
echo "The sum is: " . $sum;  // Output: The sum is: 15
?>

```

🔍 **Explanation:**

- Variables `$a` and `$b` are global.
- Inside the `add()` function, we access and add them using `$GLOBALS`.
- The result is stored as `$GLOBALS['sum']`, which becomes available as a global variable `$sum`.

---

## ✅ **Example 2: Counter with `$GLOBALS`**

```php
<?php
$count = 0;

function increment() {
    $GLOBALS['count']++;
}

increment();
increment();
echo "Count: " . $count;  // Output: Count: 2
?>

```

🔁 Each time `increment()` is called, it increases the global `$count` using `$GLOBALS`.

---

## ✅ **Example 3: Accessing Global Config Values**

```php
<?php
$siteName = "SecureWorld";
$version = "1.0";

function displayInfo() {
    echo "Welcome to " . $GLOBALS['siteName'] . " (v" . $GLOBALS['version'] . ")";
}

displayInfo();
// Output: Welcome to SecureWorld (v1.0)
?>

```

📋 You can use this method to access global configuration values across your script or project.

---

## ✅ **Example 4: Dynamic Variable Using `$GLOBALS`**

```php
<?php
$varName = "student";
$GLOBALS[$varName] = "Diya";

echo "Student Name: " . $student;  // Output: Student Name: Diya
?>

```

🎯 `$GLOBALS[$varName]` allows you to create variables dynamically, which can be useful in config-heavy applications.

---

## ✅ **Example 5: Listing All Global Variables**

```php
<?php
$username = "Diya";
$role = "Cybersecurity";

echo "<pre>";
print_r($GLOBALS);
echo "</pre>";

```

🧾 This prints all global variables currently in memory, including your custom ones.
