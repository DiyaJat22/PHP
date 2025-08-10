# File Upload in PHP

## 🧾 What Is File Upload in PHP?

PHP allows users to upload files (like images, documents, etc.) from a browser to the server using:

- An HTML form with `enctype="multipart/form-data"`
- The `$_FILES` superglobal in PHP to handle the uploaded file

---

## ✅ Step-by-Step File Upload in PHP

### 📄 1. HTML Form (`upload_form.html`)

```html
html
CopyEdit
<html>
<body>

<form action="upload.php" method="POST" enctype="multipart/form-data">
  Select a file to upload:<br><br>
  <input type="file" name="myfile"><br><br>
  <input type="submit" value="Upload File">
</form>

</body>
</html>

```

- `enctype="multipart/form-data"` is **required** for file upload.
- `name="myfile"` will be used to reference the uploaded file in PHP.

---

### 📄 2. PHP Script to Handle Upload (`upload.php`)

```php
php
CopyEdit
<?php
if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    // Check if file was uploaded
    if (isset($_FILES['myfile']) && $_FILES['myfile']['error'] === 0) {

        // Get file info
        $fileName = $_FILES['myfile']['name'];
        $fileTmp  = $_FILES['myfile']['tmp_name'];
        $fileSize = $_FILES['myfile']['size'];
        $fileType = $_FILES['myfile']['type'];

        // Optional: restrict allowed file types
        $allowedTypes = ['image/jpeg', 'image/png', 'application/pdf'];
        if (!in_array($fileType, $allowedTypes)) {
            echo "Error: Only JPG, PNG, and PDF files are allowed.";
            exit;
        }

        // Optional: limit file size (e.g., 2MB)
        if ($fileSize > 2 * 1024 * 1024) {
            echo "Error: File is too large.";
            exit;
        }

        // Set target directory
        $uploadDir = "uploads/";
        if (!is_dir($uploadDir)) {
            mkdir($uploadDir, 0755, true); // create if not exists
        }

        $destination = $uploadDir . basename($fileName);

        // Move uploaded file
        if (move_uploaded_file($fileTmp, $destination)) {
            echo "File uploaded successfully: $fileName";
        } else {
            echo "Error: Failed to move uploaded file.";
        }

    } else {
        echo "No file uploaded or upload error.";
    }
}
?>

```

---

## 🧠 What is `$_FILES`?

When a file is uploaded, `$_FILES['myfile']` contains:

```php
php
CopyEdit
[
  'name'     => 'example.jpg',       // Original file name
  'type'     => 'image/jpeg',        // MIME type
  'tmp_name' => '/tmp/php123.tmp',   // Temp file path
  'error'    => 0,                   // Error code
  'size'     => 45678                // File size in bytes
]

```

---

## 🛡️ Security Best Practices

| Risk | Fix |
| --- | --- |
| ❌ Executable file upload | ✅ Allow only specific MIME types (`image/png`, `application/pdf`, etc.) |
| ❌ Overwriting files | ✅ Rename files using `uniqid()` or timestamp |
| ❌ File injection (e.g., `.php`) | ✅ Sanitize file names |
| ❌ Huge files crashing server | ✅ Limit size in code and `php.ini` |
| ❌ Directory traversal | ✅ Use `basename()` and restrict target directory |

🔐 **Safer Destination Naming Example**:

```php
php
CopyEdit
$newName = uniqid() . "_" . basename($fileName);
$destination = $uploadDir . $newName;

```

---

## 📋 php.ini Settings to Check

You may need to adjust the following in your `php.ini` file:

```
ini
CopyEdit
file_uploads = On
upload_max_filesize = 2M
post_max_size = 8M

```

---

## ✅ Bonus: Display Uploaded Files (e.g., images)

```php
php
CopyEdit
echo "<img src='uploads/$fileName' width='300'>";

```

## ✅ **Example 1: Simple File Upload (No Validation)**

### 📄 `form.html`

```html
html
CopyEdit
<html>
<body>

<form action="upload1.php" method="POST" enctype="multipart/form-data">
  Choose a file: <input type="file" name="myfile"><br><br>
  <input type="submit" value="Upload File">
</form>

</body>
</html>

```

### 📄 `upload1.php`

```php
php
CopyEdit
<?php
if (move_uploaded_file($_FILES['myfile']['tmp_name'], "uploads/" . $_FILES['myfile']['name'])) {
    echo "File uploaded successfully!";
} else {
    echo "Upload failed!";
}
?>

```

🧠 **Note:** No checks — any file can be uploaded, so it's unsafe for real-world use.

---

## ✅ **Example 2: Secure Upload with Type and Size Validation**

### 📄 `upload2.php`

```php
php
CopyEdit
<?php
if ($_SERVER["REQUEST_METHOD"] === "POST") {
    $file = $_FILES['myfile'];

    // Validate type
    $allowedTypes = ['image/jpeg', 'image/png', 'application/pdf'];
    if (!in_array($file['type'], $allowedTypes)) {
        die("Only JPG, PNG, or PDF files allowed.");
    }

    // Validate size (max 2MB)
    if ($file['size'] > 2 * 1024 * 1024) {
        die("File too large. Max 2MB allowed.");
    }

    // Safe file name and destination
    $uploadDir = "uploads/";
    $safeName = uniqid() . "_" . basename($file['name']);
    $destination = $uploadDir . $safeName;

    if (move_uploaded_file($file['tmp_name'], $destination)) {
        echo "File uploaded as: $safeName";
    } else {
        echo "Upload failed.";
    }
}
?>

```

✅ **Security Highlights**:

- Prevents dangerous file types
- Enforces size limit
- Renames files to avoid overwriting

---

## ✅ **Example 3: Upload and Preview Image**

### 📄 `form_image.html`

```html
html
CopyEdit
<html>
<body>

<form action="upload_image.php" method="POST" enctype="multipart/form-data">
  Select an image: <input type="file" name="pic"><br><br>
  <input type="submit" value="Upload Image">
</form>

</body>
</html>

```

### 📄 `upload_image.php`

```php
php
CopyEdit
<?php
if ($_FILES['pic']['error'] === 0) {
    $fileType = $_FILES['pic']['type'];
    if (in_array($fileType, ['image/jpeg', 'image/png'])) {
        $newName = uniqid() . "_" . $_FILES['pic']['name'];
        $path = "uploads/" . $newName;
        if (move_uploaded_file($_FILES['pic']['tmp_name'], $path)) {
            echo "Uploaded!<br>";
            echo "<img src='$path' width='300'>";
        } else {
            echo "Failed to move uploaded file.";
        }
    } else {
        echo "Only images (JPG/PNG) allowed.";
    }
} else {
    echo "No file uploaded or an error occurred.";
}
?>

```

🖼️ **Output**: Displays the uploaded image on the screen.

---

