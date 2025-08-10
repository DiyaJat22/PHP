# PHP Variables

---

**Variables** in PHP are containers used to store data or information, such as numbers, text, or more complex types.

---

### Creating (Declaring) PHP Variables

In PHP, a variable name always starts with a dollar sign `$`, followed by the variable name.

```php
php
CopyEdit
$x = 5;
$y = "John";

```

- Here, `$x` holds the number `5`.
- `$y` holds the string `"John"` (note the quotes around the text value).

---

### Important Notes About Variables

- You don’t need to declare the type of a variable in advance.
- A variable is created as soon as you assign a value to it.
- Variables can have short names like `$x` or descriptive names like `$age`, `$carName`, `$totalVolume`.

---

### Rules for PHP Variable Names

- Must start with a letter (`a-z` or `A-Z`) or underscore (`_`)
- Cannot start with a number
- Can only contain letters, numbers, and underscores (e.g., `$age1`, `$car_name`)
- Variable names are **case-sensitive** (`$age` and `$AGE` are different variables)

---

### Outputting Variables

You can output variables with the `echo` statement.

Example 1: Output a string and variable together:

```php
php
CopyEdit
$txt = "W3Schools.com";
echo "I love $txt!";

```

Output:

```
css
CopyEdit
I love W3Schools.com!

```

Example 2: Output using string concatenation (`.` operator):

```php
php
CopyEdit
$txt = "W3Schools.com";
echo "I love " . $txt . "!";

```

Output:

```
css
CopyEdit
I love W3Schools.com!

```

Example 3: Output the sum of two variables:

```php
php
CopyEdit
$x = 5;
$y = 4;
echo $x + $y;

```

Output:

```
CopyEdit
9

```

---

### PHP Is Loosely Typed

- You don’t specify the variable’s data type explicitly.
- PHP automatically assigns the type based on the value you give.
- You can mix types (e.g., add strings and integers) without errors.
- From PHP 7 onwards, you can specify strict typing in functions (more advanced topic).

---

### Common Variable Data Types in PHP

PHP supports these main data types:

- **String** — text data (`"Hello"`)
- **Integer** — whole numbers (`5`)
- **Float** (double) — decimal numbers (`3.14`)
- **Boolean** — `true` or `false`
- **Array** — a list of values (`[1, 2, 3]`)
- **Object** — instances of classes
- **NULL** — no value
- **Resource** — special variable holding resources like database connections

---

### Get the Type of a Variable

Use the `var_dump()` function to see the type and value:

```php
php
CopyEdit
$x = 5;
var_dump($x);

```

Output:

```
scss
CopyEdit
int(5)

```

More examples:

```php
php
CopyEdit
var_dump(5);          // int(5)
var_dump("John");     // string(4) "John"
var_dump(3.14);       // float(3.14)
var_dump(true);       // bool(true)
var_dump([2, 3, 56]); // array(3) { ... }
var_dump(NULL);       // NULL

```

---

### Assigning Strings to Variables

Strings can be assigned using **double** or **single** quotes:

```php
php
CopyEdit
$x = "John";
echo $x;  // Outputs John

```

---

### Assign Multiple Variables at Once

You can assign the same value to multiple variables in a single line:

```php
php
CopyEdit
$x = $y = $z = "Fruit";
echo $x; // Outputs Fruit
echo $y; // Outputs Fruit
echo $z; // Outputs Fruit

```

---

Here are some simple examples of PHP variables in action:

```php
php
CopyEdit
<?php
// Declaring variables
$name = "Diya";        // A string variable
$age = 25;             // An integer variable
$height = 5.6;         // A float variable
$is_student = true;    // A boolean variable

// Output variables
echo "Name: " . $name . "<br>";
echo "Age: " . $age . "<br>";
echo "Height: " . $height . " feet<br>";
echo "Student Status: " . $is_student . "<br>";  // Will output 1 for true

// Calculate and output sum
$x = 10;
$y = 20;
$sum = $x + $y;
echo "Sum of x and y is: " . $sum;
?>

```

**Output:**

```
yaml
CopyEdit
Name: Diya
Age: 25
Height: 5.6 feet
Student Status: 1
Sum of x and y is: 30

```
