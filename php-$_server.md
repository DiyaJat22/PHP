# $_SERVER Superglobal

## 🔍 What is `$_SERVER`?

`$_SERVER` is a built-in **superglobal array in PHP** that holds information about:

- The **headers**, **paths**, and **script locations**
- The **server** and **execution environment**
- The **client request** (IP, user agent, request method, etc.)

It is automatically available in all PHP scripts — **no need to import anything**.

---

## 🧪 Common `$_SERVER` Elements with Examples

| Key | Description | Example Output |
| --- | --- | --- |
| `$_SERVER['PHP_SELF']` | Path of current script | `/form.php` |
| `$_SERVER['SERVER_NAME']` | Hostname of server | `localhost` or `www.example.com` |
| `$_SERVER['HTTP_HOST']` | Host header from the current request | `localhost` or `example.com` |
| `$_SERVER['HTTP_USER_AGENT']` | Browser details | `Mozilla/5.0 ...` |
| `$_SERVER['SCRIPT_NAME']` | Path of script | `/demo/index.php` |
| `$_SERVER['REQUEST_METHOD']` | GET or POST method used | `GET` or `POST` |
| `$_SERVER['REMOTE_ADDR']` | IP address of the client | `192.168.1.10` |

---

## ✅ Basic Example: Print Server Info

```php
<?php
echo "Current Script: " . $_SERVER['PHP_SELF'] . "<br>";
echo "Server Name: " . $_SERVER['SERVER_NAME'] . "<br>";
echo "Host: " . $_SERVER['HTTP_HOST'] . "<br>";
echo "User Agent: " . $_SERVER['HTTP_USER_AGENT'] . "<br>";
echo "Script Path: " . $_SERVER['SCRIPT_NAME'] . "<br>";
echo "Request Method: " . $_SERVER['REQUEST_METHOD'] . "<br>";
echo "Client IP: " . $_SERVER['REMOTE_ADDR'] . "<br>";
?>

```

---

## ✅ Example: Detect GET or POST Request

```php
<?php
if ($_SERVER['REQUEST_METHOD'] == 'POST') {
    echo "Form submitted using POST method.";
} else {
    echo "Please submit the form.";
}
?>

```

---

## ✅ Example: Logging User IP and Browser

```php
<?php
$ip = $_SERVER['REMOTE_ADDR'];
$browser = $_SERVER['HTTP_USER_AGENT'];

echo "Your IP is: $ip <br>";
echo "You are using: $browser";
?>

```

---

## ✅ Example: Redirect Based on Host

```php
<?php
if ($_SERVER['HTTP_HOST'] == "localhost") {
    echo "Running on local development server.";
} else {
    echo "Running on production server.";
}
?>

```

---

## 💡 Tip: `$_SERVER` is very helpful for:

- Form handling
- Security (checking IP, request method, user-agent)
- URL routing in frameworks
- Debugging environment details
- Conditional redirects (local vs live server)

## ✅ **Example 1: Display Server Information**

```php
<?php
echo "Script Name: " . $_SERVER['PHP_SELF'] . "<br>";
echo "Server Name: " . $_SERVER['SERVER_NAME'] . "<br>";
echo "HTTP Host: " . $_SERVER['HTTP_HOST'] . "<br>";
echo "User Agent: " . $_SERVER['HTTP_USER_AGENT'] . "<br>";
echo "Request Method: " . $_SERVER['REQUEST_METHOD'] . "<br>";
echo "Client IP Address: " . $_SERVER['REMOTE_ADDR'] . "<br>";
?>

```

🖥️ **Output Example:**

```
Script Name: /server_info.php
Server Name: localhost
HTTP Host: localhost
User Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64)...
Request Method: GET
Client IP Address: 127.0.0.1

```

---

## ✅ **Example 2: Detect Request Method (GET or POST)**

```php
<?php
if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    echo "Form was submitted using POST.";
} else {
    echo "This page was accessed using GET.";
}
?>

```

🧪 You can test this by submitting a form to this script with method `POST`.

---

## ✅ **Example 3: Log Client Access**

```php
<?php
$ip = $_SERVER['REMOTE_ADDR'];
$date = date("Y-m-d H:i:s");
$log = "$date - Visitor IP: $ip\n";

file_put_contents("access_log.txt", $log, FILE_APPEND);
echo "Your IP ($ip) has been logged.";
?>

```

🔐 Useful for basic security logging.

---

## ✅ **Example 4: Redirect Based on Host**

```php
<?php
if ($_SERVER['HTTP_HOST'] === "localhost") {
    echo "You are working in a local environment.";
} else {
    header("Location: https://production-site.com");
    exit();
}
?>

```

🚀 Useful for switching between development and live environments.

---

## ✅ **Example 5: Get Full URL of Current Page**

```php
<?php
$url = "http://" . $_SERVER['HTTP_HOST'] . $_SERVER['REQUEST_URI'];
echo "You are visiting: " . $url;
?>

```

📍 Output Example:

```
You are visiting: http://localhost/myproject/page.php
```
