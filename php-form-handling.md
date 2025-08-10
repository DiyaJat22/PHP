# **PHP Form Handling**

### ✅ PHP Form Handling – Complete Guide with Examples

PHP form handling is the process of **collecting user input via HTML forms**, then **processing that data using PHP**. It's one of the most common tasks in web development.

---

## 🔹 Basic Form Flow:

1. **User fills out a form in HTML**
2. **Form sends data to PHP script using GET or POST method**
3. **PHP processes the input (validates, stores, or responds)**

---

## 🔸 1. HTML Form (Frontend)

```html
<!-- form.html -->
<form action="process.php" method="POST">
  Name: <input type="text" name="name"><br>
  Email: <input type="email" name="email"><br>
  <input type="submit" value="Submit">
</form>

```

- `action="process.php"` → The PHP script to handle the data
- `method="POST"` → Sends data securely via HTTP POST

---

## 🔸 2. PHP Script to Handle Form (Backend)

```php
<!-- process.php -->
<?php
$name = $_POST['name'];
$email = $_POST['email'];

echo "Hello, $name!<br>";
echo "Your email is $email.";
?>

```

- `$_POST` is a **PHP superglobal** that stores form input sent via POST method.

---

## 🔸 3. Using `$_GET` Instead of `$_POST`

If your form uses `method="GET"`, then you use `$_GET`:

```php
<!-- process.php -->
<?php
$name = $_GET['name'];
$email = $_GET['email'];

echo "Name: $name <br>";
echo "Email: $email";
?>

```

The data will appear in the URL like:

```
process.php?name=Diya&email=diya@example.com

```

---

## 🔸 4. Secure Form Handling (Best Practices)

✅ **Validate Input**

```php
if (empty($_POST['name'])) {
    echo "Name is required";
}

```

✅ **Sanitize Input**

```php
$name = htmlspecialchars($_POST['name']);

```

✅ **Trim whitespace**

```php
$name = trim($_POST['name']);

```

✅ **Check Email Format**

```php
if (!filter_var($_POST['email'], FILTER_VALIDATE_EMAIL)) {
    echo "Invalid email format";
}

```

---

## 🔸 5. Example: Form with Validation

```php
<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $name = htmlspecialchars(trim($_POST['name']));
    $email = htmlspecialchars(trim($_POST['email']));

    if (empty($name) || empty($email)) {
        echo "All fields are required.";
    } elseif (!filter_var($email, FILTER_VALIDATE_EMAIL)) {
        echo "Invalid email format.";
    } else {
        echo "Thanks, $name. Your email is $email.";
    }
}
?>

```

---

## 🧪 Try It Yourself!

### HTML Form:

```html
<form method="post" action="handle.php">
  Name: <input type="text" name="name"><br>
  Email: <input type="text" name="email"><br>
  <input type="submit">
</form>

```

### PHP File (handle.php):

```php
<?php
$name = $_POST['name'] ?? 'Guest';
$email = $_POST['email'] ?? 'Not provided';
echo "Welcome, $name!<br>Your email: $email";
?>

```

## ✅ **Example 1: Simple Form Handling with POST**

### 🔹 `form.html`

```html
<form action="process.php" method="POST">
  Name: <input type="text" name="name"><br>
  Email: <input type="email" name="email"><br>
  <input type="submit" value="Submit">
</form>

```

### 🔹 `process.php`

```php
<?php
$name = $_POST['name'];
$email = $_POST['email'];

echo "Hello, $name!<br>";
echo "Your email is: $email";
?>

```

---

## ✅ **Example 2: Form Validation with PHP**

### 🔹 `form.html`

```html
<form action="validate.php" method="POST">
  Username: <input type="text" name="username"><br>
  Email: <input type="text" name="email"><br>
  <input type="submit" value="Send">
</form>

```

### 🔹 `validate.php`

```php
<?php
$username = trim($_POST['username']);
$email = trim($_POST['email']);

if (empty($username) || empty($email)) {
    echo "All fields are required.";
} elseif (!filter_var($email, FILTER_VALIDATE_EMAIL)) {
    echo "Invalid email format.";
} else {
    echo "Hello, $username! Your email is $email.";
}
?>

```

---

## ✅ **Example 3: GET Method Form Handling**

### 🔹 `form.html`

```html
<form action="result.php" method="GET">
  City: <input type="text" name="city"><br>
  <input type="submit" value="Search">
</form>

```

### 🔹 `result.php`

```php
<?php
$city = $_GET['city'];
echo "You searched for: $city";
?>

```

URL on submit: `result.php?city=Indore`

---

## ✅ **Example 4: Form with Radio Buttons and Checkbox**

### 🔹 `form.html`

```html
<form action="feedback.php" method="POST">
  Gender:
  <input type="radio" name="gender" value="Male"> Male
  <input type="radio" name="gender" value="Female"> Female<br>

  Interests:
  <input type="checkbox" name="hobby[]" value="Coding"> Coding
  <input type="checkbox" name="hobby[]" value="Reading"> Reading
  <input type="checkbox" name="hobby[]" value="Gaming"> Gaming<br>

  <input type="submit" value="Submit">
</form>

```

### 🔹 `feedback.php`

```php
<?php
$gender = $_POST['gender'] ?? 'Not selected';
$hobbies = $_POST['hobby'] ?? [];

echo "Gender: $gender <br>";
echo "Hobbies: " . implode(", ", $hobbies);
?>
```
