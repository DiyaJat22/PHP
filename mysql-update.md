# MySQL UPDATE Statement with PHP Examples

## What is UPDATE?

The UPDATE statement modifies existing records in a table based on a condition.

## 1. MySQLi Procedural — Simple UPDATE Query

```php
<?php
$conn = mysqli_connect("localhost", "root", "your_password", "testdb");
if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
}

$newEmail = "newdiya@example.com";
$username = "Diya";

$sql = "UPDATE users SET email = '$newEmail' WHERE username = '$username'";

if (mysqli_query($conn, $sql)) {
    echo "Record updated successfully.";
} else {
    echo "Error updating record: " . mysqli_error($conn);
}

mysqli_close($conn);
?>
```

  Warning: This method is vulnerable to SQL injection if variables come from user input. Use prepared statements instead.

---

## 2. MySQLi Procedural — UPDATE with Prepared Statement (Safe)

```php
<?php
$conn = mysqli_connect("localhost", "root", "your_password", "testdb");
if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
}

$newEmail = "newdiya@example.com";
$username = "Diya";

$stmt = mysqli_prepare($conn, "UPDATE users SET email = ? WHERE username = ?");
mysqli_stmt_bind_param($stmt, "ss", $newEmail, $username);

if (mysqli_stmt_execute($stmt)) {
    echo "Record updated successfully.";
} else {
    echo "Error updating record: " . mysqli_stmt_error($stmt);
}

mysqli_stmt_close($stmt);
mysqli_close($conn);
?>
```

---

## 3. MySQLi Object-Oriented — UPDATE with Prepared Statement

```php
<?php
$conn = new mysqli("localhost", "root", "your_password", "testdb");
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

$newEmail = "newdiya@example.com";
$username = "Diya";

$stmt = $conn->prepare("UPDATE users SET email = ? WHERE username = ?");
$stmt->bind_param("ss", $newEmail, $username);

if ($stmt->execute()) {
    echo "Record updated successfully.";
} else {
    echo "Error updating record: " . $stmt->error;
}

$stmt->close();
$conn->close();
?>
```

---

## 4. PDO — UPDATE with Prepared Statement

```php
<?php
try {
    $conn = new PDO("mysql:host=localhost;dbname=testdb;charset=utf8", "root", "your_password");
    $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

    $newEmail = "newdiya@example.com";
    $username = "Diya";

    $stmt = $conn->prepare("UPDATE users SET email = :email WHERE username = :username");
    $stmt->execute([':email' => $newEmail, ':username' => $username]);

    echo "Record updated successfully.";

} catch(PDOException $e) {
    echo "Error: " . $e->getMessage();
}
?>
```

### Important Notes:

  Always use a WHERE clause to limit which rows are updated.

  Use prepared statements to protect against SQL injection.

  You can update multiple columns like:

UPDATE users SET email = ?, status = ? WHERE username = ?

Check the affected rows if needed with mysqli_stmt_affected_rows() or $stmt->rowCount() in PDO.
