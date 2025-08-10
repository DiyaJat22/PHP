# MySQL ORDER BY with PHP Examples

## What is ORDER BY?

The ORDER BY clause sorts the result set by one or more columns, either in ascending (ASC) or descending (DESC) order.

## 1. MySQLi Procedural — ORDER BY Example

```php
<?php
$conn = mysqli_connect("localhost", "root", "your_password", "testdb");
if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
}

$sql = "SELECT id, username, email FROM users ORDER BY username ASC";  // Sort by username ascending
$result = mysqli_query($conn, $sql);

if (mysqli_num_rows($result) > 0) {
    while ($row = mysqli_fetch_assoc($result)) {
        echo $row['id'] . " - " . $row['username'] . " - " . $row['email'] . "<br>";
    }
} else {
    echo "0 results";
}

mysqli_close($conn);
?>
```

---

## 2. MySQLi Object-Oriented — ORDER BY Example

```php
<?php
$conn = new mysqli("localhost", "root", "your_password", "testdb");
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

$sql = "SELECT id, username, email FROM users ORDER BY id DESC";  // Sort by id descending
$result = $conn->query($sql);

if ($result->num_rows > 0) {
    while ($row = $result->fetch_assoc()) {
        echo $row['id'] . " - " . $row['username'] . " - " . $row['email'] . "<br>";
    }
} else {
    echo "0 results";
}

$conn->close();
?>
```

---

## 3. PDO — ORDER BY Example

```php
<?php
try {
    $conn = new PDO("mysql:host=localhost;dbname=testdb;charset=utf8", "root", "your_password");
    $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

    $stmt = $conn->query("SELECT id, username, email FROM users ORDER BY email ASC");

    $users = $stmt->fetchAll(PDO::FETCH_ASSOC);

    foreach ($users as $user) {
        echo $user['id'] . " - " . $user['username'] . " - " . $user['email'] . "<br>";
    }

} catch(PDOException $e) {
    echo "Error: " . $e->getMessage();
}
?>
```

### Notes:

Default order is ascending (ASC), but you can specify explicitly.

Use DESC to sort in descending order.

You can order by multiple columns:

ORDER BY column1 ASC, column2 DESC

Useful for sorting results by date, name, price, etc.
