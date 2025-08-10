# PHP Operators

## 🧮 PHP Operators – Complete Guide

Operators are symbols used to perform **operations on variables and values**.

---

### ✅ **Types of Operators in PHP:**

| Category | Description |
| --- | --- |
| 1. Arithmetic Operators | Perform basic math operations |
| 2. Assignment Operators | Assign values to variables |
| 3. Comparison Operators | Compare two values |
| 4. Logical Operators | Combine multiple conditions (true/false) |
| 5. Increment/Decrement | Increase or decrease values |
| 6. String Operators | Join or append strings |
| 7. Array Operators | Compare or merge arrays |
| 8. Conditional / Ternary | Shortcut for `if/else` decision-making |

---

## 🔢 1. Arithmetic Operators

| Operator | Name | Example | Result |
| --- | --- | --- | --- |
| `+` | Addition | `$x + $y` | Sum |
| `-` | Subtraction | `$x - $y` | Difference |
| `*` | Multiplication | `$x * $y` | Product |
| `/` | Division | `$x / $y` | Quotient |
| `%` | Modulus | `$x % $y` | Remainder |

```php
php
CopyEdit
$x = 10; $y = 3;
echo $x + $y; // 13

```

---

## 📝 2. Assignment Operators

| Operator | Description | Example |
| --- | --- | --- |
| `=` | Assign | `$x = 5` |
| `+=` | Add and assign | `$x += 2` |
| `-=` | Subtract and assign | `$x -= 2` |
| `*=` | Multiply and assign | `$x *= 2` |
| `/=` | Divide and assign | `$x /= 2` |

```php
php
CopyEdit
$x = 5;
$x += 3; // $x is now 8

```

---

## 🔍 3. Comparison Operators

| Operator | Meaning | Example |
| --- | --- | --- |
| `==` | Equal | `$x == $y` |
| `===` | Identical (type + value) | `$x === $y` |
| `!=` | Not equal | `$x != $y` |
| `!==` | Not identical | `$x !== $y` |
| `>` | Greater than | `$x > $y` |
| `<` | Less than | `$x < $y` |

```php
php
CopyEdit
$x = 10;
$y = "10";
var_dump($x == $y);  // true
var_dump($x === $y); // false (different types)

```

---

## 🔐 4. Logical Operators

| Operator | Meaning | Example |
| --- | --- | --- |
| `&&` | AND | `$x > 0 && $x < 100` |
| ` |  | ` |
| `!` | NOT | `!($x == 5)` |

```php
php
CopyEdit
$x = 20;
if ($x > 10 && $x < 30) {
    echo "Between 10 and 30";
}

```

---

## 🔁 5. Increment/Decrement Operators

| Operator | Description |
| --- | --- |
| `++$x` | Pre-increment |
| `$x++` | Post-increment |
| `--$x` | Pre-decrement |
| `$x--` | Post-decrement |

```php
php
CopyEdit
$x = 5;
echo ++$x; // 6
echo $x++; // 6 (then becomes 7)

```

---

## 🔤 6. String Operators

| Operator | Meaning | Example |
| --- | --- | --- |
| `.` | Concatenation | `$txt1 . $txt2` |
| `.=` | Append | `$txt1 .= $txt2` |

```php
php
CopyEdit
$greet = "Hello ";
$name = "Diya";
echo $greet . $name; // Hello Diya

```

---

## 🧩 7. Array Operators

| Operator | Meaning | Example |
| --- | --- | --- |
| `+` | Union | `$x + $y` |
| `==` | Equal arrays | `$x == $y` |
| `===` | Identical arrays | `$x === $y` |

```php
php
CopyEdit
$a = ["a" => "red", "b" => "green"];
$b = ["c" => "blue", "d" => "yellow"];
print_r($a + $b);

```

---

## ❓ 8. Ternary (Conditional) Operator

```php
php
CopyEdit
$age = 20;
echo ($age >= 18) ? "Adult" : "Minor";

```

**Output:** `Adult`

## ✅ 1. **Arithmetic Operators**

```php
php
CopyEdit
<?php
$a = 15;
$b = 4;

echo $a + $b . "<br>";  // 19 (Addition)
echo $a - $b . "<br>";  // 11 (Subtraction)
echo $a * $b . "<br>";  // 60 (Multiplication)
echo $a / $b . "<br>";  // 3.75 (Division)
echo $a % $b . "<br>";  // 3 (Modulus)
?>

```

---

## ✅ 2. **Assignment Operators**

```php
php
CopyEdit
<?php
$x = 10;
$x += 5;  // $x = $x + 5 → 15
echo $x . "<br>";

$x -= 3;  // $x = $x - 3 → 12
echo $x . "<br>";

$x *= 2;  // $x = $x * 2 → 24
echo $x . "<br>";

$x /= 6;  // $x = $x / 6 → 4
echo $x . "<br>";

$x %= 3;  // $x = $x % 3 → 1
echo $x . "<br>";
?>

```

---

## ✅ 3. **Comparison Operators**

```php
php
CopyEdit
<?php
$x = 100;
$y = "100";

var_dump($x == $y);   // true
var_dump($x === $y);  // false (different types)
var_dump($x != $y);   // false
var_dump($x !== $y);  // true
var_dump($x > 50);    // true
var_dump($x <= 99);   // false
?>

```

---

## ✅ 4. **Logical Operators**

```php
php
CopyEdit
<?php
$age = 22;
$citizen = true;

if ($age >= 18 && $citizen) {
    echo "Eligible to vote<br>";
}

if ($age < 18 || !$citizen) {
    echo "Not eligible<br>";
}

if (!($age < 18)) {
    echo "Age is 18 or above<br>";
}
?>

```

---

## ✅ 5. **Increment / Decrement Operators**

```php
php
CopyEdit
<?php
$x = 5;

echo ++$x . "<br>";  // 6 (Pre-increment)
echo $x++ . "<br>";  // 6 (Post-increment, prints 6 then becomes 7)
echo $x . "<br>";    // 7

echo --$x . "<br>";  // 6 (Pre-decrement)
echo $x-- . "<br>";  // 6 (Post-decrement)
echo $x . "<br>";    // 5
?>

```

---

## ✅ 6. **String Operators**

```php
php
CopyEdit
<?php
$first = "Cyber";
$second = "Security";

echo $first . " " . $second . "<br>";  // Cyber Security

$first .= " Expert";
echo $first . "<br>";  // Cyber Expert
?>

```

---

## ✅ 7. **Array Operators**

```php
php
CopyEdit
<?php
$a = ["a" => "red", "b" => "green"];
$b = ["c" => "blue", "d" => "yellow"];

$c = $a + $b;
print_r($c);  // Union of arrays
echo "<br>";

$d = ["a" => "red", "b" => "green"];
var_dump($a == $d);   // true
var_dump($a === $d);  // true
?>

```

---

## ✅ 8. **Ternary Operator**

```php
php
CopyEdit
<?php
$marks = 75;

$result = ($marks >= 33) ? "Pass" : "Fail";
echo $result . "<br>";

$age = 17;
echo ($age >= 18) ? "Adult" : "Minor";  // Minor
?>

```

---

## ⚡ Quick Tip for Viva or Interview:

You may be asked:

- What’s the difference between `==` and `===`?
- When do you use `&&` vs `||`?
- Can you combine operators (e.g. `$x += $y * 2`)?

Would you like a **quiz** or **flashcards** to practice these?
