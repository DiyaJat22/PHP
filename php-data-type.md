# PHP Data Type

### 🔹 **1. Scalar Data Types**

These hold **single values**.

### a) **Integer (`int`)**

- Represents whole numbers (positive or negative)
- No decimals
- Range depends on system (usually −2,147,483,648 to 2,147,483,647 on 32-bit)

**Example:**

```php
php
CopyEdit
$age = 25;
echo $age; // Output: 25

```

---

### b) **Float (`float` or `double`)**

- Represents numbers with a decimal point or in exponential form

**Example:**

```php
php
CopyEdit
$price = 99.99;
echo $price; // Output: 99.99

```

---

### c) **String (`string`)**

- A sequence of characters enclosed in quotes (single `' '` or double `" "`)

**Example:**

```php
php
CopyEdit
$name = "Diya";
echo "Hello, $name!"; // Output: Hello, Diya!

```

---

### d) **Boolean (`bool`)**

- Only two possible values: `true` or `false`
- Commonly used in conditional statements

**Example:**

```php
php
CopyEdit
$isOnline = true;
if ($isOnline) {
    echo "User is online.";
}

```

---

### 🔹 **2. Compound Data Types**

These hold **multiple values**.

### a) **Array (`array`)**

- Used to store multiple values in one variable
- Types:
    - **Indexed arrays:** Keys are numeric
    - **Associative arrays:** Keys are named

**Examples:**

```php
php
CopyEdit
// Indexed
$colors = ["red", "green", "blue"];
echo $colors[0]; // Output: red

// Associative
$user = ["name" => "Diya", "age" => 22];
echo $user["name"]; // Output: Diya

```

---

### b) **Object (`object`)**

- Instance of a class that can hold both data and functions (OOP)

**Example:**

```php
php
CopyEdit
class Student {
    public $name = "Diya";
}
$stud = new Student();
echo $stud->name; // Output: Diya

```

---

### 🔹 **3. Special Data Types**

### a) **NULL**

- A variable with no value assigned
- Used to empty a variable

**Example:**

```php
php
CopyEdit
$x = null;
var_dump($x); // Output: NULL

```

---

### b) **Resource**

- Special variable holding a reference to an external resource (like a file or database connection)
- Typically returned by functions like `fopen()`, `mysqli_connect()`

**Example:**

```php
php
CopyEdit
$file = fopen("file.txt", "r"); // $file is a resource

```

---

### Summary Table

| Type | Example | Description |
| --- | --- | --- |
| int | `10` | Whole number |
| float | `3.14` | Decimal number |
| string | `"Hello"` | Text |
| bool | `true` / `false` | Boolean value |
| array | `[1, 2, 3]` | List of values |
| object | `new ClassName()` | Class instance |
| NULL | `null` | No value |
| resource | `fopen()` result | External reference (e.g., files) |

# PHP Data Types

Variables can store data of different types, and different data types can do different things.

PHP supports the following data types:

- String
- Integer
- Float (floating point numbers - also called double)
- Boolean
- Array
- Object
- NULL
- Resource

---

# Getting the Data Type

You can get the data type of any object by using the `var_dump()` function.

# Example[Get your own PHP Server](https://www.w3schools.com/php/php_server.asp)

The `var_dump()` function returns the data type and the value:

```php
$x = 5;
var_dump($x);

```

---

# PHP String

A string is a sequence of characters, like "Hello world!".

A string can be any text inside quotes. You can use single or double quotes:

**Example**

`$x = "Hello world!";
$y = 'Hello world!';

var_dump($x);
echo "<br>";
var_dump($y);`
[Try it Yourself »](https://www.w3schools.com/php/phptryit.asp?filename=tryphp_datatypes_string)

# PHP Integer

An integer data type is a non-decimal number between -2,147,483,648 and 2,147,483,647.

Rules for integers:

- An integer must have at least one digit
- An integer must not have a decimal point
- An integer can be either positive or negative
- Integers can be specified in: decimal (base 10), hexadecimal (base 16), octal (base 8), or binary (base 2) notation

In the following example `$x` is an integer. The PHP `var_dump()` function returns the data type and value:

**Example**

`$x = 5985;
var_dump($x);`
[Try it Yourself »](https://www.w3schools.com/php/phptryit.asp?filename=tryphp_datatypes_integer)

---

# PHP Float

A float (floating point number) is a number with a decimal point or a number in exponential form.

In the following example `$x` is a float. The PHP `var_dump()` function returns the data type and value:

**Example**

`$x = 10.365;
var_dump($x);`
[Try it Yourself »](https://www.w3schools.com/php/phptryit.asp?filename=tryphp_datatypes_float)

---

# PHP Boolean

A Boolean represents two possible states: TRUE or FALSE.

**Example**

`$x = true;
var_dump($x);`
[Try it Yourself »](https://www.w3schools.com/php/phptryit.asp?filename=tryphp_datatypes_bool)

Booleans are often used in conditional testing.

You will learn more about conditional testing in the [PHP If...Else chapter](https://www.w3schools.com/php/php_if_else.asp).

---

# PHP Array

An array stores multiple values in one single variable.

In the following example `$cars` is an array. The PHP `var_dump()` function returns the data type and value:

**Example**

`$cars = array("Volvo","BMW","Toyota");
var_dump($cars);`
[Try it Yourself »](https://www.w3schools.com/php/phptryit.asp?filename=tryphp_datatypes_array)

---

# PHP Object

Classes and objects are the two main aspects of object-oriented programming.

A class is a template for objects, and an object is an instance of a class.

When the individual objects are created, they inherit all the properties and behaviors from the class, but each object will have different values for the properties.

Let's assume we have a class named `Car` that can have properties like model, color, etc. We can define variables like `$model`, `$color`, and so on, to hold the values of these properties.

When the individual objects (Volvo, BMW, Toyota, etc.) are created, they inherit all the properties and behaviors from the class, but each object will have different values for the properties.

If you create a `__construct()` function, PHP will automatically call this function when you create an object from a class.

**Example**

`class Car {
  public $color;
  public $model;
  public function __construct($color, $model) {
    $this->color = $color;
    $this->model = $model;
  }
  public function message() {
    return "My car is a " . $this->color . " " . $this->model . "!";
  }
}

$myCar = new Car("red", "Volvo");
var_dump($myCar);`
[Try it Yourself »](https://www.w3schools.com/php/phptryit.asp?filename=tryphp_datatypes_object_var_dump)

---

# PHP NULL Value

Null is a special data type which can have only one value: NULL.

A variable of data type NULL is a variable that has no value assigned to it.

**Tip:** If a variable is created without a value, it is automatically assigned a value of NULL.

Variables can also be emptied by setting the value to NULL:

**Example**

`$x = "Hello world!";
$x = null;
var_dump($x);`
[Try it Yourself »](https://www.w3schools.com/php/phptryit.asp?filename=tryphp_datatypes_null)

---

# Change Data Type

If you assign an integer value to a variable, the type will automatically be an integer.

If you assign a string to the same variable, the type will change to a string:

**Example**

`$x = 5;
var_dump($x);

$x = "Hello";
var_dump($x);`
[Try it Yourself »](https://www.w3schools.com/php/phptryit.asp?filename=tryphp_numbers2)

If you want to change the data type of an existing variable, but not by changing the value, you can use casting.

Casting allows you to change data type on variables:

**Example**

`$x = 5;
$x = (string) $x;
var_dump($x);`
[Try it Yourself »](https://www.w3schools.com/php/phptryit.asp?filename=tryphp_numbers_casting)

---

# PHP Resource

The special resource type is not an actual data type. It is the storing of a reference to functions and resources external to PHP.

A common example of using the resource data type is a database call.

We will not talk about the resource type here, since it is an advanced topic.
