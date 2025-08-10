# continue

## 🔁 `continue` Statement in PHP

### ✅ **Definition (Theory):**

The `continue` statement is used to **skip the current iteration** of a loop and **move to the next one**.

- Unlike `break`, it does **not terminate** the entire loop.
- It just **jumps to the next cycle** when a certain condition is met.

---

### ✅ **Syntax:**

```php
continue;

```

---

## 📘 **Examples**

---

### 🔹 **Example 1: `continue` in a `for` loop**

```php
<?php
for ($i = 1; $i <= 5; $i++) {
    if ($i == 3) {
        continue;
    }
    echo "Number: $i <br>";
}
?>

```

**Output:**

```
Number: 1
Number: 2
Number: 4
Number: 5

```

📝 *The value 3 is skipped.*

---

### 🔹 **Example 2: `continue` in a `while` loop**

```php
<?php
$i = 0;
while ($i < 5) {
    $i++;
    if ($i == 2) {
        continue;
    }
    echo "i = $i <br>";
}
?>

```

**Output:**

```
i = 1
i = 3
i = 4
i = 5

```

> When $i == 2, it skips the print and continues.
> 

---

### 🔹 **Example 3: `continue` in a `foreach` loop**

```php
<?php
$colors = ["Red", "Green", "Blue", "Black"];

foreach ($colors as $color) {
    if ($color == "Green") {
        continue;
    }
    echo "$color <br>";
}
?>

```

**Output:**

```
Red
Blue
Black

```

✅ *“Green” is skipped using `continue`.*

---

