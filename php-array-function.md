# PHP array functions

---

## ✅ 1. `array_push()`

**Purpose**: Adds one or more elements to the **end** of an array.

```php
<?php
$colors = ["Red", "Green"];
array_push($colors, "Blue", "Yellow");
print_r($colors);
?>

```

**Use Case**: When adding values dynamically, like user input or items to a list.

---

## ✅ 2. `array_pop()`

**Purpose**: Removes the **last** element of an array.

```php
<?php
$colors = ["Red", "Green", "Blue"];
array_pop($colors);
print_r($colors);
?>

```

**Use Case**: Stack-style (Last In First Out - LIFO) operations.

---

## ✅ 3. `array_shift()`

**Purpose**: Removes the **first** element of an array.

```php
<?php
$colors = ["Red", "Green", "Blue"];
array_shift($colors);
print_r($colors);
?>

```

**Use Case**: Queue-style (First In First Out - FIFO) behavior.

---

## ✅ 4. `array_unshift()`

**Purpose**: Adds one or more elements to the **beginning** of an array.

```php
<?php
$colors = ["Green", "Blue"];
array_unshift($colors, "Red");
print_r($colors);
?>

```

**Use Case**: Useful when maintaining order but needing to prepend data.

---

## ✅ 5. `array_merge()`

**Purpose**: Merges two or more arrays into one.

```php
<?php
$a = ["PHP", "Python"];
$b = ["Java", "C++"];
$c = array_merge($a, $b);
print_r($c);
?>

```

**Use Case**: When combining values from different sources (e.g., form + DB).

---

## ✅ 6. `in_array()`

**Purpose**: Checks if a value exists in an array.

```php
<?php
$users = ["admin", "diya"];
if (in_array("diya", $users)) {
    echo "User exists.";
}
?>

```

**Use Case**: Login verification, access checks, validation.

---

## ✅ 7. `array_keys()`

**Purpose**: Returns all the keys (index or associative) from an array.

```php
<?php
$data = ["name" => "Diya", "age" => 22];
print_r(array_keys($data));
?>

```

**Use Case**: Useful when looping over only the keys of an associative array.

---

## ✅ 8. `array_values()`

**Purpose**: Returns all the **values** from an array.

```php
<?php
$data = ["name" => "Diya", "age" => 22];
print_r(array_values($data));
?>

```

**Use Case**: When you want to ignore keys and work with just values.

---

## ✅ 9. `count()`

**Purpose**: Counts the number of elements in an array.

```php
<?php
$colors = ["Red", "Green", "Blue"];
echo count($colors); // Output: 3
?>

```

**Use Case**: Validating input, pagination, loops.

---

## ✅ 10. `sort()`

**Purpose**: Sorts an array in ascending order (values only).

```php
<?php
$numbers = [4, 2, 7, 1];
sort($numbers);
print_r($numbers);
?>

```

**Use Case**: Displaying data in a sorted manner (e.g., scores).

---

## ✅ 11. `rsort()`

**Purpose**: Sorts an array in descending order.

```php
<?php
$numbers = [4, 2, 7, 1];
rsort($numbers);
print_r($numbers);
?>

```

---

## ✅ 12. `array_reverse()`

**Purpose**: Reverses the order of elements.

```php
<?php
$colors = ["Red", "Green", "Blue"];
print_r(array_reverse($colors));
?>

```

---

## ✅ 13. `array_slice()`

**Purpose**: Extracts a portion of the array.

```php
<?php
$fruits = ["Apple", "Banana", "Mango", "Orange"];
print_r(array_slice($fruits, 1, 2)); // Banana, Mango
?>

```

**Use Case**: Pagination, previews, trimming data.

---

## ✅ 14. `array_search()`

**Purpose**: Searches the array for a value and returns its key/index.

```php
<?php
$colors = ["Red", "Green", "Blue"];
echo array_search("Green", $colors); // 1
?>

```

---

## ✅ 15. `array_unique()`

**Purpose**: Removes duplicate values from an array.

```php
<?php
$nums = [1, 2, 2, 3, 3, 3];
print_r(array_unique($nums));
?>

```
