# PHP Form Validation

## 🔹 Why Form Validation Is Important

- Prevents SQL Injection
- Prevents XSS attacks
- Ensures required fields are filled
- Ensures data format is correct (email, numbers, etc.)
- Reduces garbage or incorrect data in the database

---

## 🔹 Types of Validation

1. **Client-side Validation** (HTML/JavaScript) – Fast, but can be bypassed.
2. **Server-side Validation** (PHP) – Secure and mandatory.

---

## 🔹 Basic PHP Form Validation Steps

1. Check if the form is submitted.
2. Clean the input (remove extra spaces, slashes, and convert special characters).
3. Validate each input field.
4. Show errors if found.

---

## 🔹 Sample HTML Form

```html
<form method="POST" action="<?php echo htmlspecialchars($_SERVER["PHP_SELF"]); ?>">
  Name: <input type="text" name="name"><br>
  Email: <input type="text" name="email"><br>
  Website: <input type="text" name="website"><br>
  Comment: <textarea name="comment"></textarea><br>
  Gender:
  <input type="radio" name="gender" value="female">Female
  <input type="radio" name="gender" value="male">Male
  <br><br>
  <input type="submit" name="submit" value="Submit">
</form>

```

---

## 🔹 PHP Script for Validation

```php
<?php
// Define variables and set to empty
$name = $email = $gender = $comment = $website = "";
$nameErr = $emailErr = $genderErr = "";

if ($_SERVER["REQUEST_METHOD"] == "POST") {
  // Validate name
  if (empty($_POST["name"])) {
    $nameErr = "Name is required";
  } else {
    $name = clean_input($_POST["name"]);
    if (!preg_match("/^[a-zA-Z-' ]*$/", $name)) {
      $nameErr = "Only letters and white space allowed";
    }
  }

  // Validate email
  if (empty($_POST["email"])) {
    $emailErr = "Email is required";
  } else {
    $email = clean_input($_POST["email"]);
    if (!filter_var($email, FILTER_VALIDATE_EMAIL)) {
      $emailErr = "Invalid email format";
    }
  }

  // Website (optional)
  if (!empty($_POST["website"])) {
    $website = clean_input($_POST["website"]);
    if (!filter_var($website, FILTER_VALIDATE_URL)) {
      $websiteErr = "Invalid URL";
    }
  }

  // Comment (optional)
  if (!empty($_POST["comment"])) {
    $comment = clean_input($_POST["comment"]);
  }

  // Gender
  if (empty($_POST["gender"])) {
    $genderErr = "Gender is required";
  } else {
    $gender = clean_input($_POST["gender"]);
  }
}

// Function to clean input
function clean_input($data) {
  $data = trim($data);             // Remove extra spaces
  $data = stripslashes($data);     // Remove backslashes
  $data = htmlspecialchars($data); // Prevent XSS
  return $data;
}
?>

```

---

## 🔹 Display Error Messages

You can echo the errors near the form fields:

```php
Name: <input type="text" name="name">
<span style="color:red;"><?php echo $nameErr; ?></span>

```

---

## 🔹 Additional Validations (Optional)

- Password strength (using regex)
- Matching password and confirm-password
- Phone number pattern
- Max/Min length
- Custom validation rules

---

## 🔹 Summary

- Always sanitize input using `htmlspecialchars()` or `filter_var()`.
- Use regex or PHP built-in filters like `FILTER_VALIDATE_EMAIL`.
- Never trust client-side validation alone.

## ✅ Example 1: **Simple Form with Name and Email Validation**

### 🔹 HTML + PHP in One File

```php
<!DOCTYPE html>
<html>
<head>
  <title>Simple PHP Form Validation</title>
</head>
<body>

<?php
$name = $email = "";
$nameErr = $emailErr = "";

if ($_SERVER["REQUEST_METHOD"] == "POST") {
  // Name
  if (empty($_POST["name"])) {
    $nameErr = "Name is required";
  } else {
    $name = clean_input($_POST["name"]);
    if (!preg_match("/^[a-zA-Z-' ]*$/", $name)) {
      $nameErr = "Only letters and spaces allowed";
    }
  }

  // Email
  if (empty($_POST["email"])) {
    $emailErr = "Email is required";
  } else {
    $email = clean_input($_POST["email"]);
    if (!filter_var($email, FILTER_VALIDATE_EMAIL)) {
      $emailErr = "Invalid email format";
    }
  }
}

function clean_input($data) {
  $data = trim($data);
  $data = stripslashes($data);
  $data = htmlspecialchars($data);
  return $data;
}
?>

<h2>PHP Form Validation Example</h2>
<form method="post" action="<?php echo htmlspecialchars($_SERVER["PHP_SELF"]); ?>">
  Name: <input type="text" name="name" value="<?php echo $name; ?>">
  <span style="color:red;">* <?php echo $nameErr; ?></span>
  <br><br>
  Email: <input type="text" name="email" value="<?php echo $email; ?>">
  <span style="color:red;">* <?php echo $emailErr; ?></span>
  <br><br>
  <input type="submit" name="submit" value="Submit">
</form>

<?php
if ($name && $email && !$nameErr && !$emailErr) {
  echo "<h3>Form Submitted Successfully!</h3>";
  echo "Name: $name<br>";
  echo "Email: $email";
}
?>

</body>
</html>

```

---

## ✅ Example 2: **Form with More Fields (URL, Comment, Gender)**

This one validates:

- Name
- Email
- Website URL (optional)
- Comment (optional)
- Gender (required)

```php
<?php
$name = $email = $website = $comment = $gender = "";
$nameErr = $emailErr = $genderErr = $websiteErr = "";

if ($_SERVER["REQUEST_METHOD"] == "POST") {
  if (empty($_POST["name"])) {
    $nameErr = "Name is required";
  } else {
    $name = clean_input($_POST["name"]);
    if (!preg_match("/^[a-zA-Z-' ]*$/", $name)) {
      $nameErr = "Only letters and spaces allowed";
    }
  }

  if (empty($_POST["email"])) {
    $emailErr = "Email is required";
  } else {
    $email = clean_input($_POST["email"]);
    if (!filter_var($email, FILTER_VALIDATE_EMAIL)) {
      $emailErr = "Invalid email format";
    }
  }

  if (!empty($_POST["website"])) {
    $website = clean_input($_POST["website"]);
    if (!filter_var($website, FILTER_VALIDATE_URL)) {
      $websiteErr = "Invalid URL";
    }
  }

  $comment = clean_input($_POST["comment"]);

  if (empty($_POST["gender"])) {
    $genderErr = "Gender is required";
  } else {
    $gender = clean_input($_POST["gender"]);
  }
}

function clean_input($data) {
  return htmlspecialchars(stripslashes(trim($data)));
}
?>

<form method="post" action="<?php echo htmlspecialchars($_SERVER["PHP_SELF"]); ?>">
  Name: <input type="text" name="name" value="<?php echo $name; ?>">
  <span style="color:red;">* <?php echo $nameErr; ?></span>
  <br><br>

  Email: <input type="text" name="email" value="<?php echo $email; ?>">
  <span style="color:red;">* <?php echo $emailErr; ?></span>
  <br><br>

  Website: <input type="text" name="website" value="<?php echo $website; ?>">
  <span style="color:red;"><?php echo $websiteErr; ?></span>
  <br><br>

  Comment: <textarea name="comment"><?php echo $comment; ?></textarea>
  <br><br>

  Gender:
  <input type="radio" name="gender" value="female" <?php if ($gender == "female") echo "checked"; ?>>Female
  <input type="radio" name="gender" value="male" <?php if ($gender == "male") echo "checked"; ?>>Male
  <span style="color:red;">* <?php echo $genderErr; ?></span>
  <br><br>

  <input type="submit" name="submit" value="Submit">
</form>

```

---

## ✅ Example 3: **Login Form with Password Validation**

```php
<?php
$username = $password = "";
$usernameErr = $passwordErr = "";

if ($_SERVER["REQUEST_METHOD"] == "POST") {
  if (empty($_POST["username"])) {
    $usernameErr = "Username is required";
  } else {
    $username = clean_input($_POST["username"]);
  }

  if (empty($_POST["password"])) {
    $passwordErr = "Password is required";
  } else {
    $password = clean_input($_POST["password"]);
    if (strlen($password) < 6) {
      $passwordErr = "Password must be at least 6 characters long";
    }
  }

  if (!$usernameErr && !$passwordErr) {
    echo "Login successful (just a simulation)";
  }
}

function clean_input($data) {
  return htmlspecialchars(stripslashes(trim($data)));
}
?>

<form method="post">
  Username: <input type="text" name="username" value="<?php echo $username; ?>">
  <span style="color:red;">* <?php echo $usernameErr; ?></span><br><br>

  Password: <input type="password" name="password">
  <span style="color:red;">* <?php echo $passwordErr; ?></span><br><br>

  <input type="submit" value="Login">
</form>
```
