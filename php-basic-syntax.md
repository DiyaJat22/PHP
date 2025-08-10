# PHP Syntax

---

**PHP** (Hypertext Preprocessor) is a server-side scripting language used to create dynamic web pages. When a PHP script runs, it executes on the server, and only the resulting plain HTML is sent back to the user's browser.

---

## Basic PHP Syntax

- A PHP script can be embedded anywhere inside an HTML document.
- A PHP script starts with `<?php` and ends with `?>`.

Example:

```php
<?php
  // PHP code goes here
?>
```

  PHP files typically have the extension .php.

  A PHP file usually contains HTML code mixed with PHP code.

## Example: Simple PHP Script

This example demonstrates a PHP file that contains both HTML and PHP code. It uses the built-in PHP function echo to display text on a web page.

```php
<!DOCTYPE html>
<html>
  <body>
    <h1>My first PHP page</h1>
    <?php
      echo "Hello World!";
    ?>
  </body>
</html>
```

  When this file is requested, the server runs the PHP code and sends the following HTML to the browser:

```php
<h1>My first PHP page</h1>
Hello World!
```

PHP Case Sensitivity

PHP keywords, functions, classes, and user-defined functions are NOT case-sensitive.

For example, echo, ECHO, and EcHo all work the same.

## Example: Case-Insensitive Keywords

```php
<!DOCTYPE html>
<html>
  <body>
    <?php
      ECHO "Hello World!<br>";
      echo "Hello World!<br>";
      EcHo "Hello World!<br>";
    ?>
  </body>
</html>
```

All three echo statements will output "Hello World!" with line breaks.

### Important Note:

While PHP keywords and functions are case-insensitive, variable names are case-sensitive.

## Example: Variables Are Case-Sensitive

```php
<!DOCTYPE html>
<html>
  <body>
    <?php
      $color = "red";
      echo "My car is " . $color . "<br>";   // Outputs: My car is red
      echo "My house is " . $COLOR . "<br>"; // Undefined variable, outputs nothing or error
      echo "My boat is " . $coLOR . "<br>";  // Undefined variable, outputs nothing or error
    ?>
  </body>
</html>
```
  $color, $COLOR, and $coLOR are treated as three different variables.

  Only $color has been defined; the others will cause errors or output nothing.

  ### Summary

- PHP code is embedded within `<?php ... ?>` tags inside an HTML document.
- PHP scripts execute on the server, sending only the resulting HTML to the client.
- PHP keywords and functions are **not case-sensitive**.
- Variable names in PHP **are case-sensitive**; `$var` and `$VAR` are different.
- PHP files typically use the `.php` extension.
- PHP allows mixing of HTML and PHP code to create dynamic webpages.
