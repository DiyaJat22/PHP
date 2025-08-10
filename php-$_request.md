# $_REQUEST Superglobal

## 🧾 What is `$_REQUEST`?

The `$_REQUEST` superglobal is an associative array in PHP that **collects data** from:

- `$_GET`
- `$_POST`
- `$_COOKIE`

> It is a general-purpose variable that retrieves input data regardless of the HTTP method or cookies.
> 

---

## 🟡 Syntax

```php
$_REQUEST['key'];

```

---

## ✅ When to Use `$_REQUEST`?

Use `$_REQUEST` when you:

- Don’t know (or don’t care) whether data was sent via GET, POST, or COOKIE.
- Want a **quick way** to fetch input for testing or small applications.

⚠️ **Not recommended for secure or large applications** — it's better to use `$_POST` or `$_GET` specifically to reduce ambiguity and improve security.

---

## 📌 Example 1: Using `$_REQUEST` with a Form

### 📄 `form.html`

```html
<html>
<body>

<h2>Request Form</h2>
<form action="process.php" method="POST">
  Username: <input type="text" name="username"><br><br>
  Age: <input type="text" name="age"><br><br>
  <input type="submit" value="Submit">
</form>

</body>
</html>

```

### 📄 `process.php`

```php
<?php
$username = $_REQUEST['username'];
$age = $_REQUEST['age'];

echo "Username: $username<br>";
echo "Age: $age";
?>

```

🔁 You can change `method="POST"` to `GET`, and it will still work because `$_REQUEST` handles both.

---

## 📌 Example 2: `$_REQUEST` with URL Parameters

You can send data via URL like this:

```
http://localhost/process.php?city=Indore&country=India

```

### 📄 `process.php`

```php
<?php
$city = $_REQUEST['city'];
$country = $_REQUEST['country'];

echo "City: $city<br>";
echo "Country: $country";
?>

```

🖥️ **Output:**

```
City: Indore
Country: India

```

---

## 📌 Example 3: Mixing GET, POST, and COOKIE

```php
<?php
setcookie("user", "Diya", time()+3600); // Set cookie
?>

<form method="POST" action="welcome.php">
    <input type="text" name="email">
    <input type="submit">
</form>

```

### 📄 `welcome.php`

```php
<?php
echo "Email: " . $_REQUEST['email'] . "<br>";
echo "User from cookie: " . $_REQUEST['user'];
?>

```

---

## ⚠️ Security Note

Avoid using `$_REQUEST` for:

- Login forms
- Sensitive data
- Input validation

✅ Instead, **explicitly use `$_POST`, `$_GET`, or `$_COOKIE`** so you know exactly where the data is coming from.

## ✅ **Example 1: Using `$_REQUEST` with a POST Form**

### 📄 `form1.html`

```html
<html>
<body>

<h2>Form using POST method</h2>
<form action="request_post.php" method="POST">
  Name: <input type="text" name="name"><br><br>
  Age: <input type="text" name="age"><br><br>
  <input type="submit" value="Submit">
</form>

</body>
</html>

```

### 📄 `request_post.php`

```php
<?php
$name = $_REQUEST['name'];
$age = $_REQUEST['age'];

echo "Your name is: $name <br>";
echo "Your age is: $age";
?>

```

🧪 **Input**: Name = Diya, Age = 21

🖥️ **Output**:

```
Your name is: Diya
Your age is: 21

```

---

## ✅ **Example 2: Using `$_REQUEST` with GET Parameters (URL)**

You can open this URL in your browser:

```
http://localhost/request_get.php?city=Indore&state=Madhya%20Pradesh

```

### 📄 `request_get.php`

```php
<?php
$city = $_REQUEST['city'];
$state = $_REQUEST['state'];

echo "City: $city <br>";
echo "State: $state";
?>

```

🖥️ **Output**:

```
City: Indore
State: Madhya Pradesh

```

---

## ✅ **Example 3: Using `$_REQUEST` with Cookies**

### 📄 `set_cookie.php`

```php
<?php
setcookie("user", "Diya", time() + 3600); // valid for 1 hour
echo "Cookie is set. <a href='read_cookie.php'>Go to read_cookie.php</a>";
?>

```

### 📄 `read_cookie.php`

```php
<?php
$user = $_REQUEST['user'];  // fetches cookie value

echo "User from cookie: $user";
?>

```

🖥️ **Output**:

```
User from cookie: Diya

```

> ⚠️ Note: Cookies are only accessible on the next request/page load after being set.
> 

---
