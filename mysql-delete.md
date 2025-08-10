# MySQL DELETE Statement with PHP Examples

## What is DELETE?

The DELETE statement removes rows from a table based on a specified condition.

## 1. MySQLi Procedural — Delete Rows with Condition

```php
<?php
$conn = mysqli_connect("localhost", "root", "your_password", "testdb");
if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
}

$username = "Diya";

$sql = "DELETE FROM users WHERE username = '$username'";

if (mysqli_query($conn, $sql)) {
    echo "Record deleted successfully.";
} else {
    echo "Error deleting record: " . mysqli_error($conn);
}

mysqli_close($conn);
?>
```

  Warning: The above example is vulnerable to SQL injection if $username comes from user input. Use prepared statements instead.

## 2. MySQLi Procedural — Delete with Prepared Statement (Safe)

```php
<?php
$conn = mysqli_connect("localhost", "root", "your_password", "testdb");
if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
}

$username = "Diya";

$stmt = mysqli_prepare($conn, "DELETE FROM users WHERE username = ?");
mysqli_stmt_bind_param($stmt, "s", $username);

if (mysqli_stmt_execute($stmt)) {
    echo "Record deleted successfully.";
} else {
    echo "Error deleting record: " . mysqli_stmt_error($stmt);
}

mysqli_stmt_close($stmt);
mysqli_close($conn);
?>
```

---

## 3. MySQLi Object-Oriented — Delete with Prepared Statement

```php
<?php
$conn = new mysqli("localhost", "root", "your_password", "testdb");
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

$username = "Diya";

$stmt = $conn->prepare("DELETE FROM users WHERE username = ?");
$stmt->bind_param("s", $username);

if ($stmt->execute()) {
    echo "Record deleted successfully.";
} else {
    echo "Error deleting record: " . $stmt->error;
}

$stmt->close();
$conn->close();
?>
```

---

## 4. PDO — Delete with Prepared Statement

```php
<?php
try {
    $conn = new PDO("mysql:host=localhost;dbname=testdb;charset=utf8", "root", "your_password");
    $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

    $username = "Diya";

    $stmt = $conn->prepare("DELETE FROM users WHERE username = :username");
    $stmt->execute([':username' => $username]);

    echo "Record deleted successfully.";

} catch(PDOException $e) {
    echo "Error: " . $e->getMessage();
}
?>
```

### Important Notes:

  Always use WHERE clause to avoid deleting all rows accidentally.

  Use prepared statements to prevent SQL injection.

  For deleting all rows in a table, use TRUNCATE TABLE tablename (faster and resets auto-increment).

