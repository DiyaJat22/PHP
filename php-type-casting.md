# PHP Type Casting — Explained with Examples

Sometimes in PHP, you want to **convert a variable from one data type to another**. This is called **casting**.

You can cast variables using these syntax forms:

| Cast to | Syntax | Description |
| --- | --- | --- |
| String | `(string)` | Convert variable to string |
| Integer | `(int)` | Convert variable to integer |
| Float | `(float)` | Convert variable to floating point |
| Boolean | `(bool)` | Convert variable to boolean |
| Array | `(array)` | Convert variable to array |
| Object | `(object)` | Convert variable to object |
| NULL | `(unset)` | Convert variable to NULL |

---

## 1. Cast to **String**

Converts the value to a string.

```php
php
CopyEdit
<?php
$a = 5;       // integer
$b = 5.34;    // float
$c = true;    // boolean
$d = NULL;    // null

$a = (string)$a;
$b = (string)$b;
$c = (string)$c;
$d = (string)$d;

var_dump($a); // string(1) "5"
var_dump($b); // string(4) "5.34"
var_dump($c); // string(1) "1"  (true becomes "1")
var_dump($d); // string(0) ""   (NULL becomes empty string)
?>

```

---

## 2. Cast to **Integer**

Converts the value to an integer.

- Numbers in strings convert until invalid character.
- Non-numeric strings convert to 0.
- Boolean true → 1, false → 0.

```php
php
CopyEdit
<?php
$a = 5.7;             // float
$b = "25 kilometers"; // string
$c = "kilometers 25"; // string
$d = true;            // boolean
$e = NULL;            // null

$a = (int)$a;  // 5
$b = (int)$b;  // 25
$c = (int)$c;  // 0
$d = (int)$d;  // 1
$e = (int)$e;  // 0

var_dump($a, $b, $c, $d, $e);
?>

```

---

## 3. Cast to **Float**

Converts the value to a floating point number.

```php
php
CopyEdit
<?php
$a = 5;              // integer
$b = "25.7 kilometers"; // string
$c = "kilometers 25";   // string
$d = true;           // boolean
$e = NULL;           // null

$a = (float)$a;  // 5.0
$b = (float)$b;  // 25.7
$c = (float)$c;  // 0.0
$d = (float)$d;  // 1.0
$e = (float)$e;  // 0.0

var_dump($a, $b, $c, $d, $e);
?>

```

---

## 4. Cast to **Boolean**

Converts the value to true or false.

- `0`, `0.0`, `""` (empty string), `"0"`, `NULL`, and `false` become `false`.
- All other values become `true`.

```php
php
CopyEdit
<?php
$a = 5;      // integer
$b = 0;      // integer zero
$c = -1;     // negative integer
$d = 0.1;    // float
$e = "";     // empty string
$f = "hello"; // string
$g = NULL;    // null

var_dump((bool)$a); // true
var_dump((bool)$b); // false
var_dump((bool)$c); // true
var_dump((bool)$d); // true
var_dump((bool)$e); // false
var_dump((bool)$f); // true
var_dump((bool)$g); // false
?>

```

---

## 5. Cast to **Array**

Converts the value to an array.

- Scalars become one-element indexed arrays.
- NULL becomes an empty array.
- Objects convert to associative arrays with property names as keys.

```php
php
CopyEdit
<?php
$a = 5;       // integer
$b = "hello"; // string
$c = NULL;    // null

$arrA = (array)$a; // array(1) { [0]=> int(5) }
$arrB = (array)$b; // array(1) { [0]=> string(5) "hello" }
$arrC = (array)$c; // array(0) {}

var_dump($arrA, $arrB, $arrC);

// Object example
class Car {
  public $color = "red";
  public $model = "Toyota";
}

$car = new Car();
$arrCar = (array)$car;

var_dump($arrCar);
?>

```

---

## 6. Cast to **Object**

Converts the value to an object.

- Scalars become objects with a `scalar` property.
- Arrays become objects with keys as property names.
- NULL becomes an empty object.

```php
php
CopyEdit
<?php
$a = 5;      // integer
$b = ["a" => 1, "b" => 2]; // associative array
$c = NULL;   // null

$objA = (object)$a;
$objB = (object)$b;
$objC = (object)$c;

var_dump($objA);
var_dump($objB);
var_dump($objC);
?>

```

---

## 7. Cast to **NULL**

Converts the value to `NULL`.

```php
php
CopyEdit
<?php
$a = 5;
$b = "hello";

$a = (unset)$a;
$b = (unset)$b;

var_dump($a); // NULL
var_dump($b); // NULL
?>

```

---

# Exercise

**What is the correct syntax to cast a float into a string?**

```php
php
CopyEdit
// Correct:
$x = (string) 5.6;

// Incorrect:
// $x = tostring(5.6);
// $x = (5.6).tostr();

```

---

Here's **one complete PHP script** demonstrating all the type castings together with clear output using `var_dump()` for each cast type:

```php
php
CopyEdit
<?php
// Original variables
$a = 5;               // integer
$b = 5.34;            // float
$c = "25 kilometers";  // string (numeric + text)
$d = "kilometers 25";  // string (text + numeric)
$e = true;            // boolean
$f = NULL;            // null
$g = ["x" => 10, "y" => 20]; // associative array
$h = new stdClass();  // object
$h->name = "PHP";
$h->version = 8;

// Cast to STRING
echo "=== Cast to STRING ===\n";
var_dump((string)$a);
var_dump((string)$b);
var_dump((string)$c);
var_dump((string)$d);
var_dump((string)$e);
var_dump((string)$f);
echo "\n";

// Cast to INTEGER
echo "=== Cast to INTEGER ===\n";
var_dump((int)$a);
var_dump((int)$b);
var_dump((int)$c);  // parses numeric prefix
var_dump((int)$d);  // no numeric prefix → 0
var_dump((int)$e);
var_dump((int)$f);
echo "\n";

// Cast to FLOAT
echo "=== Cast to FLOAT ===\n";
var_dump((float)$a);
var_dump((float)$b);
var_dump((float)$c);
var_dump((float)$d);
var_dump((float)$e);
var_dump((float)$f);
echo "\n";

// Cast to BOOLEAN
echo "=== Cast to BOOLEAN ===\n";
var_dump((bool)$a);
var_dump((bool)0);       // false example
var_dump((bool)$b);
var_dump((bool)$f);
var_dump((bool)"");      // empty string → false
var_dump((bool)"hello"); // non-empty string → true
echo "\n";

// Cast to ARRAY
echo "=== Cast to ARRAY ===\n";
var_dump((array)$a);
var_dump((array)$b);
var_dump((array)$c);
var_dump((array)$f);  // NULL → empty array
var_dump((array)$h);  // object → associative array
echo "\n";

// Cast to OBJECT
echo "=== Cast to OBJECT ===\n";
var_dump((object)$a);
var_dump((object)$g);  // array → object
var_dump((object)$f);  // NULL → empty object
echo "\n";

// Cast to NULL (unset)
echo "=== Cast to NULL ===\n";
var_dump((unset)$a);
var_dump((unset)$g);
var_dump((unset)$f);
?>

```

---

### What this script does:

- Shows all main data types casted to **string, integer, float, boolean, array, object, and NULL**
- Includes examples with numbers, strings with numbers, booleans, NULL, arrays, and objects
- Uses `var_dump()` to show type and value clearly for each cast
