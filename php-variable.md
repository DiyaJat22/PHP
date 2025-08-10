# PHP Variables Scope

## PHP Variables Scope

In PHP, **variable scope** refers to the part of the script where a variable is accessible or can be used. Variables can be declared anywhere, but their availability depends on their scope.

### Types of Variable Scope in PHP:

1. **Local Scope**  
2. **Global Scope**  
3. **Static Scope**  

---

### 1. Local Scope

- A variable declared **inside a function** has **local scope**.  
- It can only be accessed and used **within that function**.  
- Trying to use it outside the function will cause an error.  

### Example: Local Variable

```php
<?php
function myTest() {
  $x = 5; // Local variable
  echo "Variable x inside function is: $x<br>";
}

myTest();

// Trying to access $x outside the function will cause an error
echo "Variable x outside function is: $x<br>";  // Undefined variable error
?>
```

## 2. Global Scope

  - A variable declared outside any function has global scope.

  - It can only be accessed outside functions by default.

  - Inside a function, the variable is not accessible unless specified.

### Example: Global Variable

```php
<?php
$x = 5; // Global variable

function myTest() {
  // This will not work because $x is global and inaccessible inside the function by default
  echo "Variable x inside function is: $x<br>";
}

myTest();

echo "Variable x outside function is: $x<br>";
?>
```

To access a global variable inside a function, you need to use the global keyword or the $GLOBALS array.

### Using the global Keyword:

```php
<?php
$x = 5;
$y = 10;

function myTest() {
  global $x, $y;
  $y = $x + $y;
}

myTest();
echo $y; // Outputs: 15
?>
```

### Using the $GLOBALS Array:

```php
<?php
$x = 5;
$y = 10;

function myTest() {
  $GLOBALS['y'] = $GLOBALS['x'] + $GLOBALS['y'];
}

myTest();
echo $y; // Outputs: 15
?>
```

## 3. Static Scope

  - Normally, local variables inside functions are destroyed after the function finishes execution.

  - Sometimes you want a local variable to retain its value between function calls.

  - Use the static keyword to declare such variables.

### Example: Static Variable

```php
<?php
function myTest() {
  static $x = 0;  // Static variable
  echo $x . "<br>";
  $x++;
}

myTest();  // Outputs: 0
myTest();  // Outputs: 1
myTest();  // Outputs: 2
?>
```

Here, $x keeps its value between function calls, but it is still local to the function.

### Exercise Explanation:

```php
<?php
$name = 'Linus';

function myTest() {
  $name = 'Tobias';
}

myTest();
echo $name;
?>
```

### What will be the output?

  - Output: Linus

### Explanation:

  - Inside myTest(), $name is a local variable with value 'Tobias'.

  - It does not affect the global $name variable.

  - When you echo $name; outside the function, it outputs the global $name which is 'Linus'.

### Summary

| Scope  | Description                              | Accessibility                                 | Example Usage                           |
|--------|------------------------------------------|-----------------------------------------------|----------------------------------------|
| Local  | Variables declared inside a function     | Accessible only inside that function          | `$x = 5;` inside function               |
| Global | Variables declared outside any function  | Accessible globally, except inside functions unless specified | `$x = 5;` outside function; use `global $x;` inside function |
| Static | Local variables that retain their value between calls | Accessible only inside that function          | `static $x = 0;` inside function        |
