## 🍪 What is `$_COOKIE`?

`$_COOKIE` is a **PHP superglobal associative array** used to **access cookies** sent by the client (browser) to the server.

Cookies are small pieces of data stored on the user's computer and are used to:

- Store login status
- Track user preferences
- Maintain sessions
- Implement simple user tracking

---

## 🟢 Syntax

```php
$_COOKIE['key'];

```

---

## ✅ How to Use Cookies in PHP

### 1. **Set a Cookie**

```php
setcookie(name, value, expire, path, domain, secure, httponly);

```

- `name` – Cookie name
- `value` – Cookie value
- `expire` – Expiry time (in seconds, using `time()`)
- Optional: `path`, `domain`, `secure`, `httponly`

---

## 📌 Example 1: Set and Read a Cookie

### 📄 `set_cookie.php`

```php
<?php
setcookie("user", "Diya", time() + 3600); // Expires in 1 hour
echo "Cookie 'user' is set! <br>";
echo "<a href='get_cookie.php'>Click here to read the cookie</a>";
?>

```

### 📄 `get_cookie.php`

```php
<?php
if (isset($_COOKIE["user"])) {
    echo "Welcome back, " . $_COOKIE["user"];
} else {
    echo "User cookie is not set!";
}
?>

```

🖥️ **Output:**

```
Welcome back, Diya

```

---

## 📌 Example 2: Cookie Expiration

### 📄 `expire_cookie.php`

```php
<?php
// Set cookie to expire in the past
setcookie("user", "", time() - 3600);
echo "Cookie 'user' has been deleted.";
?>

```

---

## 📌 Example 3: Multiple Cookies

### 📄 `multi_cookie.php`

```php
<?php
setcookie("name", "Diya", time() + 3600);
setcookie("language", "PHP", time() + 3600);
?>

<a href="read_multi_cookie.php">Read Cookies</a>

```

### 📄 `read_multi_cookie.php`

```php
<?php
echo "Name: " . $_COOKIE["name"] . "<br>";
echo "Language: " . $_COOKIE["language"];
?>

```

---

## 🛡️ Best Practices for Cookies

| Tip | Description |
| --- | --- |
| `httponly=true` | Prevent JavaScript access (protect against XSS) |
| `secure=true` | Only send cookie over HTTPS |
| Use `json_encode()` for arrays | Store structured data like arrays in a cookie |
| Validate before use | Always check if a cookie is set (`isset()`) |

## ✅ **Example 1: Set and Read a Simple Cookie**

### 📄 `set_cookie.php`

```php
<?php
// Set cookie named "user" with value "Diya", expires in 1 hour
setcookie("user", "Diya", time() + 3600);
echo "Cookie 'user' is set!<br>";
echo "<a href='read_cookie.php'>Click to read cookie</a>";
?>

```

### 📄 `read_cookie.php`

```php
php
CopyEdit
<?php
if (isset($_COOKIE["user"])) {
    echo "Welcome, " . $_COOKIE["user"];
} else {
    echo "No cookie found.";
}
?>

```

🖥️ **Output (after visiting both pages):**

```
Welcome, Diya

```

---

## ✅ **Example 2: Delete a Cookie**

### 📄 `delete_cookie.php`

```php
<?php
// Delete the "user" cookie by setting expiry in the past
setcookie("user", "", time() - 3600);
echo "Cookie 'user' has been deleted.";
?>

```

---

## ✅ **Example 3: Store User Preferences (Theme)**

### 📄 `set_theme.php`

```php
<?php
$theme = $_GET['theme']; // "light" or "dark"
setcookie("theme", $theme, time() + (86400 * 30)); // 30 days
echo "Theme set to $theme. <a href='home.php'>Go to home</a>";
?>

```

Visit:

```
http://localhost/set_theme.php?theme=dark

```

### 📄 `home.php`

```php
<?php
$theme = isset($_COOKIE['theme']) ? $_COOKIE['theme'] : 'light';
?>

<!DOCTYPE html>
<html>
<body style="background-color: <?php echo $theme == 'dark' ? '#333' : '#fff'; ?>; color: <?php echo $theme == 'dark' ? '#fff' : '#000'; ?>;">

<h1>Welcome!</h1>
<p>Your theme is set to <strong><?php echo $theme; ?></strong>.</p>

<a href="set_theme.php?theme=light">Light Theme</a> |
<a href="set_theme.php?theme=dark">Dark Theme</a>

</body>
</html>

```

---

