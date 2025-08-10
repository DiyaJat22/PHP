# $_FILES Superglobal

## 📦 What is `$_FILES`?

`$_FILES` is a **superglobal associative array** in PHP used to collect file upload data when a form is submitted using `method="POST"` and `enctype="multipart/form-data"`.

---

## 📋 Structure of `$_FILES`

When a user uploads a file, PHP fills the `$_FILES` array with the following keys:

```php
$_FILES['input_name']['name']      // Original file name
$_FILES['input_name']['type']      // MIME type (e.g., image/jpeg)
$_FILES['input_name']['tmp_name']  // Temporary file name stored on server
$_FILES['input_name']['error']     // Error code (0 = no error)
$_FILES['input_name']['size']      // File size in bytes

```

---

## ✅ Example 1: HTML Form to Upload a File

```html
<!-- upload_form.html -->
<html>
<body>
  <form action="upload.php" method="POST" enctype="multipart/form-data">
    Select file to upload:
    <input type="file" name="myfile">
    <input type="submit" value="Upload">
  </form>
</body>
</html>

```

---

## ✅ Example 2: PHP Script to Handle Upload

```php
<!-- upload.php -->
<?php
if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    if (isset($_FILES['myfile']) && $_FILES['myfile']['error'] == 0) {
        $fileName = $_FILES['myfile']['name'];
        $fileTmp = $_FILES['myfile']['tmp_name'];
        $fileSize = $_FILES['myfile']['size'];
        $fileType = $_FILES['myfile']['type'];

        // Upload to 'uploads/' folder
        $destination = "uploads/" . basename($fileName);

        if (move_uploaded_file($fileTmp, $destination)) {
            echo "File uploaded successfully: " . $fileName;
        } else {
            echo "Failed to upload the file.";
        }
    } else {
        echo "No file selected or an error occurred.";
    }
}
?>

```

🛡️ Make sure the `uploads/` folder exists and has the right permissions (`chmod 755 uploads` or `chmod 777 uploads` for testing).

---

## 🧪 Output of `$_FILES` (for debugging)

```php
echo "<pre>";
print_r($_FILES);
echo "</pre>";

```

**Example Output:**

```
Array
(
    [myfile] => Array
        (
            [name] => sample.jpg
            [type] => image/jpeg
            [tmp_name] => /tmp/phpXyZ12A
            [error] => 0
            [size] => 512000
        )
)

```

---

## 🔐 Tips for Secure File Uploads

1. **Validate file type:** Allow only certain file types (e.g., JPG, PNG).
2. **Limit file size:** Use `$_FILES['myfile']['size']`.
3. **Rename uploaded files:** Avoid using original names to prevent overwriting or code execution.
4. **Set proper folder permissions:** Never make `uploads/` folder writable by everyone on production.
5. **Use `move_uploaded_file()`** instead of `copy()` for security.

## ✅ **Example 1: Basic File Upload**

### 🔹 HTML Form (`upload_form.html`)

```html
<form action="upload_basic.php" method="POST" enctype="multipart/form-data">
  Choose a file: <input type="file" name="myfile">
  <input type="submit" value="Upload">
</form>

```

### 🔹 PHP Script (`upload_basic.php`)

```php
<?php
if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    if (isset($_FILES['myfile']) && $_FILES['myfile']['error'] === 0) {
        $name = $_FILES['myfile']['name'];
        $tmp  = $_FILES['myfile']['tmp_name'];
        $destination = "uploads/" . basename($name);

        if (move_uploaded_file($tmp, $destination)) {
            echo "File uploaded successfully: $name";
        } else {
            echo "Error moving file.";
        }
    } else {
        echo "No file uploaded or an error occurred.";
    }
}
?>

```

---

## ✅ **Example 2: File Upload with Validation (Size + Type)**

```php
<?php
$allowedTypes = ['image/jpeg', 'image/png', 'application/pdf'];
$maxSize = 2 * 1024 * 1024; // 2 MB

if (isset($_FILES['myfile'])) {
    $file = $_FILES['myfile'];

    if ($file['error'] === 0) {
        if (in_array($file['type'], $allowedTypes)) {
            if ($file['size'] <= $maxSize) {
                $uploadPath = "uploads/" . basename($file['name']);
                if (move_uploaded_file($file['tmp_name'], $uploadPath)) {
                    echo "File uploaded: " . $file['name'];
                } else {
                    echo "Upload failed.";
                }
            } else {
                echo "File too large. Max size: 2MB.";
            }
        } else {
            echo "Invalid file type.";
        }
    } else {
        echo "Upload error code: " . $file['error'];
    }
}
?>

```

---

## ✅ **Example 3: Rename Uploaded File to Prevent Overwrites**

```php
<?php
if (isset($_FILES['myfile'])) {
    $file = $_FILES['myfile'];
    $extension = pathinfo($file['name'], PATHINFO_EXTENSION);
    $newName = uniqid("upload_", true) . "." . $extension;

    $destination = "uploads/" . $newName;

    if (move_uploaded_file($file['tmp_name'], $destination)) {
        echo "Uploaded and renamed file: $newName";
    } else {
        echo "Upload failed.";
    }
}
?>

```

---

