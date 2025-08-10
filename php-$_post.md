# $_POST superglobal

## 🧾 What is `$_POST`?

`$_POST` is a **PHP superglobal** used to **collect form data** sent via the **HTTP POST method**. It stores the submitted values as an **associative array**.

---

## 🛠️ When to Use `$_POST`?

- When you want to **submit form data securely**
- For data that should **not appear in the URL**
- For **large data submissions** (unlike GET, which has URL size limits)

---

## ✅ Basic Example: Simple Form with POST Method

### 📄 `form.html`

```html
<html>
<body>

<form action="welcome_post.php" method="POST">
  Name: <input type="text" name="name"><br><br>
  Email: <input type="text" name="email"><br><br>
  <input type="submit" value="Submit">
</form>

</body>
</html>

```

### 📄 `welcome_post.php`

```php
<html>
<body>

Welcome <?php echo $_POST["name"]; ?><br>
Your email address is: <?php echo $_POST["email"]; ?>

</body>
</html>

```

### 🔍 What happens?

- The form sends data to `welcome_post.php` using the POST method.
- PHP uses `$_POST['name']` and `$_POST['email']` to access the submitted values.

---

## 📦 Output Example

If the user enters:

- Name: `Diya`
- Email: `diya@example.com`

Then the output will be:

```
Welcome Diya
Your email address is: diya@example.com

```

---

## 🔐 Why Use POST Instead of GET?

| Feature | GET | POST |
| --- | --- | --- |
| URL visible? | Yes (`?name=Diya`) | No |
| Max data size | Limited (2KB–8KB) | Larger (up to MBs) |
| Used for? | Links, searches | Login, forms, secure data |
| Security | Less secure (exposed) | More secure (in body) |

---

## 🛡️ Security Tip

Before using `$_POST` data, always **validate and sanitize** it to avoid attacks like:

- **XSS (Cross-site scripting)**: use `htmlspecialchars()`
- **SQL Injection**: use prepared statements (with PDO or MySQLi)

Example:

```php
$name = htmlspecialchars($_POST["name"]);

```

---

## ⚙️ Real-World Use Case: Login Form with POST

### 📄 `login.html`

```html
<form action="login.php" method="POST">
  Username: <input type="text" name="username"><br>
  Password: <input type="password" name="password"><br>
  <input type="submit" value="Login">
</form>

```

### 📄 `login.php`

```php
<?php
$user = $_POST['username'];
$pass = $_POST['password'];

if ($user === 'admin' && $pass === 'secret') {
    echo "Welcome, Admin!";
} else {
    echo "Invalid credentials.";
}
?>

```

## ✅ **Example 1: Basic Form Submission with `$_POST`**

### 📄 `form1.html`

```html
<html>
<body>

<h2>Basic Form</h2>
<form action="process1.php" method="POST">
  Name: <input type="text" name="name"><br><br>
  Age: <input type="text" name="age"><br><br>
  <input type="submit" value="Submit">
</form>

</body>
</html>

```

### 📄 `process1.php`

```php
<?php
$name = $_POST['name'];
$age = $_POST['age'];

echo "Hello, $name!<br>";
echo "You are $age years old.";
?>

```

🧪 **Input**: Name: Diya, Age: 25

🖥️ **Output**:

```
Hello, Diya!
You are 21 years old.

```

---

## ✅ **Example 2: Sanitizing User Input with `htmlspecialchars()`**

To prevent Cross-Site Scripting (XSS), sanitize data before printing.

### 📄 `process2.php`

```php
<?php
$name = htmlspecialchars($_POST['name']);
$comment = htmlspecialchars($_POST['comment']);

echo "Thank you, $name.<br>";
echo "Your comment: $comment";
?>

```

### 🧪 Input via form:

```html
<form action="process2.php" method="POST">
  Name: <input type="text" name="name"><br>
  Comment: <textarea name="comment"></textarea><br>
  <input type="submit">
</form>

```

🧪 **User enters**:

```
Name: Diya
Comment: <script>alert('XSS');</script>

```

🛡️ **Output is safely shown as**:

```
Thank you, Diya.
Your comment: &lt;script&gt;alert('XSS');&lt;/script&gt;

```

---

## ✅ **Example 3: Simple Login System using `$_POST`**

### 📄 `login.html`

```html
<form action="login.php" method="POST">
  Username: <input type="text" name="username"><br>
  Password: <input type="password" name="password"><br>
  <input type="submit" value="Login">
</form>

```

### 📄 `login.php`

```php
<?php
$user = $_POST['username'];
$pass = $_POST['password'];

if ($user === "admin" && $pass === "password123") {
    echo "Login successful! Welcome, $user.";
} else {
    echo "Login failed. Incorrect username or password.";
}
?>

```

🧪 **Input**: Username: `admin`, Password: `password123`

🖥️ **Output**:

```
Login successful! Welcome, admin.

```
