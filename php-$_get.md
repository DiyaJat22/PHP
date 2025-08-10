## 🔍 What is `$_GET` in PHP?

`$_GET` is a **PHP superglobal** array that stores **data sent via the URL (query string)** using the **HTTP GET method**.

This is often used to:

- Pass variables in hyperlinks
- Receive form input
- Trigger actions or filters in web apps

---

## ✅ Example 1: Query String via URL

### 📌 URL:

```html
<a href="demo.php?subject=PHP&web=W3schools.com">Test $_GET</a>

```

- This link sends:
    
    ```
    subject = PHP
    web = W3schools.com
    
    ```
    

### 📜 PHP file: `demo.php`

```php
<html>
<body>

<?php
echo "Study " . $_GET['subject'] . " at " . $_GET['web'];
?>

</body>
</html>

```

### 🖥️ Output:

```
Study PHP at W3schools.com

```

🧠 **Why It’s Useful:**

Great for dynamic pages like:

- `page.php?id=5`
- `search.php?term=linux`

---

## ✅ Example 2: HTML Form Using `GET`

### 📄 HTML Form:

```html
<html>
<body>

<form action="welcome_get.php" method="GET">
  Name: <input type="text" name="name">
  E-mail: <input type="text" name="email">
  <input type="submit">
</form>

</body>
</html>

```

### 💡 How It Works:

When you type:

```
Name: Diya
Email: diya@example.com

```

And click submit, the browser sends:

```
welcome_get.php?name=Diya&email=diya@example.com

```

### 📜 PHP in `welcome_get.php`

```php
<html>
<body>

Welcome <?php echo $_GET["name"]; ?><br>
Your email address is: <?php echo $_GET["email"]; ?>

</body>
</html>

```

### 🖥️ Output:

```
Welcome Diya
Your email address is: diya@example.com

```

---

## 🧠 How Does the Data Flow?

1. Browser makes a **GET request** to `welcome_get.php` with query parameters.
2. `$_GET['name']` contains `Diya`, and `$_GET['email']` contains `diya@example.com`.
3. PHP script processes and prints it on screen.

---

## ⚠️ Security Risks with `$_GET`

| Threat | Example | How to Prevent |
| --- | --- | --- |
| 🔥 **XSS (Cross-Site Scripting)** | `?name=<script>alert(1)</script>` | Use `htmlspecialchars()` |
| 📂 **LFI (Local File Inclusion)** | `?file=../../etc/passwd` | Validate/whitelist filenames |
| 📜 **Exposing Sensitive Data** | Email/password in URL | Use `POST` method instead |

### ✅ Secure Output Example

```php
<?php
echo "Welcome " . htmlspecialchars($_GET["name"]);
?>

```

---

## 🎯 When to Use `$_GET`

| Use Case | Example |
| --- | --- |
| Search queries | `search.php?query=php` |
| Sorting | `products.php?sort=price_asc` |
| Filtering | `blog.php?category=linux` |
| Tracking campaigns | `landing.php?utm_source=twitter` |
| Pagination | `page=2` |

---

## 🧪 Practice Task (Try it Yourself!)

1. Create a file `form.html` with a form using method `GET`
2. Create `response.php` to collect:
    - Name
    - Age
    - Favorite language
3. Use `htmlspecialchars()` in PHP to sanitize inputs

---

## ✅ **Example 1: Basic URL Parameters**

### 🔗 Link:

```html
<a href="example1.php?name=Diya&city=Indore">Click Me</a>

```

### 📄 `example1.php`

```php
<html>
<body>

<?php
echo "Hello " . $_GET['name'] . " from " . $_GET['city'] . "!";
?>

</body>
</html>

```

### 🖥️ Output:

```
Hello Diya from Indore!

```

---

## ✅ **Example 2: Search Function (Simulated)**

### 🔗 URL:

```html
<a href="search.php?query=linux">Search for Linux</a>

```

### 📄 `search.php`

```php
<html>
<body>

<?php
echo "You searched for: " . htmlspecialchars($_GET['query']);
?>

</body>
</html>

```

### 🖥️ Output:

```
You searched for: linux

```

> ✅ htmlspecialchars() is used to prevent XSS if the user types <script>alert(1)</script>
> 

---

## ✅ **Example 3: Form Using `GET` Method**

### 📄 `form.html`

```html
<html>
<body>

<form action="form_result.php" method="GET">
  Name: <input type="text" name="name"><br>
  Age: <input type="text" name="age"><br>
  <input type="submit" value="Submit">
</form>

</body>
</html>

```

### 📄 `form_result.php`

```php
<html>
<body>

<?php
$name = htmlspecialchars($_GET['name']);
$age = htmlspecialchars($_GET['age']);

echo "Welcome, $name!<br>";
echo "You are $age years old.";
?>

</body>
</html>

```

### 🖥️ Output (after submitting the form):

```
Welcome, Diya!
You are 23 years old.

```

---

## ✅ **Example 4: File Viewer (Unsafe & Safe Version)**

### ❌ Insecure Version (LFI Risk!)

```php
<?php
$file = $_GET['page'];
include($file); // BAD: could include /etc/passwd or ../../config.php
?>

```

### ✅ Secure Version (Whitelist allowed pages)

```php
<?php
$pages = ['home', 'about', 'contact'];
$page = $_GET['page'];

if (in_array($page, $pages)) {
    include("$page.php");
} else {
    echo "Invalid page!";
}
?>

```

> 🔐 Always validate user input when using it in file operations.
> 

---

## ✅ **Example 5: Calculator Using `GET`**

### 📄 `calc.html`

```html
<form action="calc.php" method="GET">
  Number 1: <input type="text" name="num1"><br>
  Number 2: <input type="text" name="num2"><br>
  <input type="submit" value="Add">
</form>

```

### 📄 `calc.php`

```php
<?php
$num1 = (int) $_GET['num1'];
$num2 = (int) $_GET['num2'];
$sum = $num1 + $num2;

echo "Result: " . $sum;
?>

```

### 🖥️ Output (if input is 3 and 4):

```
Result: 7

```

---

## 🛡️ Tip for You (Security Focus)

When using `$_GET`:

- Always **validate** and **sanitize** input
- Never use user input directly in file paths, SQL, or HTML output
- Use functions like:
    - `htmlspecialchars()` – to prevent XSS
    - `filter_input(INPUT_GET, 'var', FILTER_SANITIZE_STRING)` – for cleaner input
    - Typecasting `(int)`, `(float)` – to enforce data type
