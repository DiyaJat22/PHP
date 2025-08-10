# **PHP Numbers**

# PHP Numbers Explained

PHP supports different types of numbers:

### 1. Integers

- Whole numbers without decimals, like `2`, `256`, `10358`.
- Range depends on system (usually ±2 billion on 32-bit, much larger on 64-bit).
- Can be decimal, hexadecimal (start with `0x`), octal (start with `0`), or binary (start with `0b`).
- Use functions like `is_int()` to check if a variable is an integer.

### 2. Floats (or Doubles)

- Numbers with decimal points or exponential notation, like `5.34`, `7.64E+5`.
- Store larger or fractional numbers.
- Use `is_float()` to check if a variable is a float.

### 3. Numeric Strings

- Strings containing numbers, like `"25"`.
- PHP can treat them as numbers in operations.
- Check with `is_numeric()`.

### 4. Infinity

- Numbers larger than `PHP_FLOAT_MAX` are considered infinite.
- Check with `is_infinite()`.

### 5. NaN (Not a Number)

- Result of invalid math operations (e.g., `acos(8)`).
- Check with `is_nan()`.

### Casting to Integer

- You can convert floats or numeric strings to integers using `(int)` or `intval()`.

---

# PHP Numbers with Different Examples

### 1. **Integer Examples**

```php
php
CopyEdit
$x = 100;              // decimal integer
$y = 0x1A;             // hexadecimal integer (26 decimal)
$z = 075;              // octal integer (61 decimal)
$w = 0b1010;           // binary integer (10 decimal)

echo "Decimal: $x<br>";
echo "Hexadecimal 0x1A = $y<br>";
echo "Octal 075 = $z<br>";
echo "Binary 0b1010 = $w<br>";

```

### 2. **Float Examples**

```php
php
CopyEdit
$a = 12.345;           // normal float
$b = 1.5e3;            // scientific notation = 1500
$c = 7E-2;             // scientific notation = 0.07

echo "Float a = $a<br>";
echo "Float b = $b<br>";
echo "Float c = $c<br>";

```

### 3. **Numeric Strings**

```php
php
CopyEdit
$str1 = "12345";           // numeric string (integer)
$str2 = "12.345";          // numeric string (float)
$str3 = "7.5e2";           // numeric string with scientific notation

echo "Is '$str1' numeric? ";
var_dump(is_numeric($str1));  // true

echo "Is '$str2' numeric? ";
var_dump(is_numeric($str2));  // true

echo "Is '$str3' numeric? ";
var_dump(is_numeric($str3));  // true

```

### 4. **Infinity Example**

```php
php
CopyEdit
$bigNum = 1.0e309;  // Larger than PHP_FLOAT_MAX

echo "Value: ";
var_dump($bigNum);  // float(INF)

echo "Is infinite? ";
var_dump(is_infinite($bigNum));  // true

```

### 5. **NaN (Not a Number) Example**

```php
php
CopyEdit
$invalidCalc = sqrt(-25);   // square root of negative number

echo "Value: ";
var_dump($invalidCalc);    // float(NAN)

echo "Is NaN? ";
var_dump(is_nan($invalidCalc));  // true

```

### 6. **Casting Examples**

```php
php
CopyEdit
$floatNum = 56.78;
$stringNum = "123abc";

// Cast float to int
$castInt1 = (int)$floatNum;   // 56

// Cast string to int (stops at first non-digit character)
$castInt2 = (int)$stringNum;  // 123

echo "Float $floatNum cast to int: $castInt1<br>";
echo "String \"$stringNum\" cast to int: $castInt2<br>";

```

---

# Summary

| Concept | Example Value(s) | Output/Behavior |
| --- | --- | --- |
| Integer | 100, 0x1A, 075, 0b1010 | Different base formats for integers |
| Float | 12.345, 1.5e3, 7E-2 | Decimal and scientific notation floats |
| Numeric String | "12345", "12.345", "7.5e2" | Strings that look like numbers |
| Infinity | 1.0e309 | Exceed max float → Infinity |
| NaN | sqrt(-25) | Invalid math operation returns NaN |
| Casting | 56.78, "123abc" | Convert floats/strings to integers |

# Combined Example

```php
php
CopyEdit
<?php
// Integers
$a = 5;
echo "Variable a: ";
var_dump($a);  // int(5)
echo "<br>Is a an integer? ";
var_dump(is_int($a));  // true

// Floats
$b = 5.34;
echo "Variable b: ";
var_dump($b);  // float(5.34)
echo "<br>Is b a float? ";
var_dump(is_float($b));  // true

// Numeric String
$c = "25";
echo "Variable c: ";
var_dump($c);  // string(2) "25"
echo "<br>Is c numeric? ";
var_dump(is_numeric($c));  // true

// Infinity example
$inf = 1.9e411; // larger than PHP_FLOAT_MAX
echo "Variable inf: ";
var_dump($inf);  // float(INF)
echo "<br>Is inf infinite? ";
var_dump(is_infinite($inf));  // true

// NaN example (invalid math operation)
$nan = acos(8);
echo "Variable nan: ";
var_dump($nan);  // float(NAN)
echo "<br>Is nan NaN? ";
var_dump(is_nan($nan));  // true

// Casting float and string to int
$float_num = 23465.768;
$int_cast1 = (int)$float_num;
echo "<br>Float $float_num cast to int: $int_cast1";

$string_num = "23465.768";
$int_cast2 = (int)$string_num;
echo "<br>String \"$string_num\" cast to int: $int_cast2";
?>

```

---

# What you learn from this example:

- How to create integers, floats, and numeric strings.
- How to check their types with `is_int()`, `is_float()`, `is_numeric()`.
- What happens with values larger than max float (`Infinity`).
- How invalid math results in `NaN`.
- How to convert floats or numeric strings into integers using casting.
