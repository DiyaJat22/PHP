# PHP Superglobals

## 🧠 What Are PHP Superglobals?

**Superglobals** are built-in variables in PHP that are **always accessible**, regardless of scope — meaning you can use them inside functions, classes, or files without needing to declare them as global.

They are **associative arrays** (key-value pairs) used to collect input, environment info, server data, cookies, and more.

---

## 🔟 List of PHP Superglobals

| Superglobal | Description |
| --- | --- |
| `$_GET` | Captures data sent via the URL (query parameters) |
| `$_POST` | Captures data sent via an HTML form using the POST method |
| `$_REQUEST` | Combines data from `$_GET`, `$_POST`, and `$_COOKIE` |
| `$_SESSION` | Stores user session data across multiple pages |
| `$_COOKIE` | Stores small data on the client side |
| `$_FILES` | Handles file uploads from forms |
| `$_SERVER` | Provides server and execution environment info |
| `$_ENV` | Environment variables (like from shell or `.env` files) |
| `$_GLOBALS` | Accesses global variables from anywhere in the script |
| `$_PHP_SELF` | Returns the filename of the currently executing script |

---

## 🔍 Examples & Use Cases

### 1. 🟩 `$_GET`

Used for query strings (e.g., `index.php?page=about`):

```php
<?php
echo $_GET['page']; // Outputs "about"
?>

```

> 🔒 Vulnerability Risk: If not sanitized, it can lead to XSS or Local File Inclusion (LFI).
> 

---

### 2. 🟨 `$_POST`

Used for form submissions:

```php
<form method="POST">
  <input name="username">
</form>

<?php
echo $_POST['username'];
?>

```

> 🔒 Risk: Can be used to bypass client-side validation or inject SQL/XSS.
> 

---

### 3. 🟦 `$_REQUEST`

Accepts both `GET`, `POST`, and `COOKIE` data:

```php
<?php
echo $_REQUEST['input'];
?>

```

> 🔒 Risk: It's ambiguous—difficult to control input source; not recommended in secure apps.
> 

---

### 4. 🟥 `$_SESSION`

Stores data between page loads:

```php
<?php
session_start();
$_SESSION['user'] = 'Diya';
echo $_SESSION['user'];
?>

```

> 🔐 Secure sessions are key for login systems. Protect with session fixation and cookie flags (HttpOnly, Secure).
> 

---

### 5. 🟧 `$_COOKIE`

Data stored on the client side:

```php
<?php
setcookie("user", "Diya", time()+3600);
echo $_COOKIE['user'];
?>

```

> 🔒 Risk: Can be tampered by attackers—validate everything from cookies.
> 

---

### 6. 🟪 `$_FILES`

Used for file uploads:

```php
<?php
move_uploaded_file($_FILES["file"]["tmp_name"], "uploads/" . $_FILES["file"]["name"]);
?>

```

> 🔥 Critical to sanitize file names and validate file type, size, and extension to avoid RCE or web shell uploads.
> 

---

### 7. 🟫 `$_SERVER`

Information about headers, paths, and script locations:

```php
<?php
echo $_SERVER['HTTP_USER_AGENT']; // Browser info
echo $_SERVER['REQUEST_METHOD'];  // GET or POST
?>

```

> 🔒 Use carefully — can be spoofed (e.g., User-Agent, Referer) for social engineering or phishing.
> 

---

### 8. 🟨 `$_ENV`

Accesses environment variables:

```php
<?php
echo $_ENV['PATH'];
?>

```

> 📦 Often used with .env configs in frameworks like Laravel or Symfony.
> 

---

### 9. 🟦 `$_GLOBALS`

Access global variables inside functions:

```php
<?php
$name = "Diya";
function greet() {
  echo $GLOBALS['name'];
}
greet(); // Outputs: Diya
?>

```

> ⚠️ Avoid excessive use — can lead to messy and insecure code.
> 

---

### 🔹 `$_PHP_SELF`

Returns the current script path:

```php
<form action="<?php echo $_PHP_SELF; ?>" method="POST">

```

> 🔒 If not escaped (htmlspecialchars()), it can lead to XSS via self-reflected form actions.
> 

---

## ⚠️ Security Risks and Best Practices

| Superglobal | Common Risks | Secure Practice |
| --- | --- | --- |
| `$_GET`, `$_POST` | XSS, SQLi, LFI | Input validation, sanitization |
| `$_FILES` | Arbitrary file upload | Whitelist extensions, use `basename()`, limit size |
| `$_SESSION` | Session hijacking | Regenerate ID, use HTTPS, set cookie flags |
| `$_COOKIE` | Cookie tampering | Hash/sign cookie data |
| `$_SERVER` | Header spoofing | Don’t rely on headers for security |

---

## 🛡️ Pentester Usage in OSCP/CTF/Bug Bounty

During recon or exploitation:

- Look for pages using `$_GET['file']`, `$_GET['page']` → **LFI**
- Test login forms using `$_POST` → **SQLi**, **auth bypass**
- Check file upload forms using `$_FILES` → **Web Shell RCE**
- Analyze cookies → decode and modify `$_COOKIE` values
- Observe session handling via `$_SESSION` → **Session fixation**
