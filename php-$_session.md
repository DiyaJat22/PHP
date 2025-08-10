# $_SESSION Superglobal

## 🔐 What is `$_SESSION`?

`$_SESSION` is a PHP **superglobal array** used to **store data on the server** across multiple pages.

Unlike cookies (stored on the client), session data is kept on the **server**, making it **more secure** and better for storing sensitive information like login credentials or preferences.

---

## 🛠️ How Sessions Work

1. Start the session using `session_start()`
2. Set session variables using `$_SESSION['key'] = value`
3. Access session variables from any page after session is started
4. Destroy the session when done (e.g., logout)

---

## ✅ Basic Example: Store User Name

### 📄 `start_session.php`

```php
<?php
session_start(); // Always at the top
$_SESSION["username"] = "Diya";
echo "Session started and username is set. <a href='read_session.php'>Go to next page</a>";
?>

```

### 📄 `read_session.php`

```php
<?php
session_start();
echo "Welcome, " . $_SESSION["username"];
?>

```

🖥️ **Output:**

```
CopyEdit
Welcome, Diya

```

---

## ✅ Example 2: Login and Logout Using Sessions

### 📄 `login.php`

```php
<?php
session_start();

if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $username = $_POST["username"];
    $_SESSION["user"] = $username;
    header("Location: dashboard.php");
}
?>

<form method="post">
  Username: <input type="text" name="username">
  <input type="submit" value="Login">
</form>

```

### 📄 `dashboard.php`

```php
<?php
session_start();
if (!isset($_SESSION["user"])) {
    header("Location: login.php");
    exit();
}
echo "Hello, " . $_SESSION["user"] . "!<br>";
echo "<a href='logout.php'>Logout</a>";
?>

```

### 📄 `logout.php`

```php
<?php
session_start();
session_unset(); // Remove all session variables
session_destroy(); // Destroy the session
echo "You are logged out. <a href='login.php'>Login again</a>";
?>

```

---

## ✅ Example 3: Session Counter

### 📄 `counter.php`

```php
<?php
session_start();

if (!isset($_SESSION['counter'])) {
    $_SESSION['counter'] = 1;
} else {
    $_SESSION['counter']++;
}

echo "You have visited this page " . $_SESSION['counter'] . " times.";
?>

```

---

## 🧠 Summary of Session Functions

| Function | Description |
| --- | --- |
| `session_start()` | Starts a session or resumes an existing one |
| `$_SESSION['key']` | Stores/retrieves session data |
| `session_unset()` | Removes all session variables |
| `session_destroy()` | Ends the session completely |

---

## 🛡️ Why Use Sessions Instead of Cookies?

| Feature | Cookies | Sessions |
| --- | --- | --- |
| Stored in | Client (Browser) | Server |
| Size limit | 4KB | Large (server-side memory based) |
| Secure | Less secure (can be manipulated) | More secure |
| Best for | Preferences, tracking | Login data, user identity |

## ✅ Example 1: Simple Session Storage

### 📄 `set_session.php`

```php
<?php
session_start(); // Start the session

$_SESSION["name"] = "Diya";
$_SESSION["role"] = "Cyber Security Student";

echo "Session variables are set. <a href='get_session.php'>Go to next page</a>";
?>

```

### 📄 `get_session.php`

```php
<?php
session_start(); // Resume session

echo "Welcome, " . $_SESSION["name"] . "<br>";
echo "Role: " . $_SESSION["role"];
?>

```

🖥️ **Output:**

```
Welcome, Diya
Role: Cyber Security Student

```

---

## ✅ Example 2: Page Visit Counter

### 📄 `visit_counter.php`

```php
<?php
session_start();

if (!isset($_SESSION['count'])) {
    $_SESSION['count'] = 1;
} else {
    $_SESSION['count']++;
}

echo "You have visited this page " . $_SESSION['count'] . " times.";
?>
```


🖥️ **Output after refreshing:**

```
You have visited this page 1 times.
You have visited this page 2 times.
...

```

---

## ✅ Example 3: Simple Login and Logout System

### 📄 `login.php`

```php
<?php
session_start();

if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $user = $_POST["username"];
    $_SESSION["user"] = $user;
    header("Location: dashboard.php");
    exit();
}
?>

<form method="post">
    Username: <input type="text" name="username">
    <input type="submit" value="Login">
</form>

```

### 📄 `dashboard.php`

```php
<?php
session_start();

if (!isset($_SESSION["user"])) {
    echo "Access denied. <a href='login.php'>Login</a>";
    exit();
}

echo "Welcome, " . $_SESSION["user"] . "!<br>";
echo "<a href='logout.php'>Logout</a>";
?>

```

### 📄 `logout.php`

```php
<?php
session_start();
session_unset();  // Remove session variables
session_destroy(); // End session

echo "You have been logged out. <a href='login.php'>Login again</a>";
?>
```
