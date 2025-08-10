# MySQL LIMIT Clause with PHP Examples

## What is LIMIT?

LIMIT restricts the number of rows returned from a query result.

### Syntax:

```php
SELECT columns FROM table LIMIT number;
```

To skip rows and then limit:

```php
SELECT columns FROM table LIMIT offset, count;
```

## 1. MySQLi Procedural — Simple LIMIT Example

```php
<?php
$conn = mysqli_connect("localhost", "root", "your_password", "testdb");
if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
}

$sql = "SELECT id, username, email FROM users ORDER BY id ASC LIMIT 5";  // Get first 5 rows
$result = mysqli_query($conn, $sql);

if (mysqli_num_rows($result) > 0) {
    while ($row = mysqli_fetch_assoc($result)) {
        echo $row['id'] . " - " . $row['username'] . " - " . $row['email'] . "<br>";
    }
} else {
    echo "No results found";
}

mysqli_close($conn);
?>
```

---

## 2. MySQLi Procedural — LIMIT with OFFSET

```php
<?php
$conn = mysqli_connect("localhost", "root", "your_password", "testdb");
if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
}

$offset = 5;
$limit = 5;

$sql = "SELECT id, username, email FROM users ORDER BY id ASC LIMIT $offset, $limit";  // Skip first 5 rows, then next 5 rows
$result = mysqli_query($conn, $sql);

if (mysqli_num_rows($result) > 0) {
    while ($row = mysqli_fetch_assoc($result)) {
        echo $row['id'] . " - " . $row['username'] . " - " . $row['email'] . "<br>";
    }
} else {
    echo "No results found";
}

mysqli_close($conn);
?>
```

---

## 3. PDO — LIMIT Example with Prepared Statements

```php
<?php
try {
    $conn = new PDO("mysql:host=localhost;dbname=testdb;charset=utf8", "root", "your_password");
    $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

    $limit = 5;
    $offset = 0;

    // Note: LIMIT and OFFSET cannot be bound as parameters in some PDO drivers, so use intval to sanitize
    $stmt = $conn->prepare("SELECT id, username, email FROM users ORDER BY id ASC LIMIT :offset, :limit");
    $stmt->bindValue(':offset', (int)$offset, PDO::PARAM_INT);
    $stmt->bindValue(':limit', (int)$limit, PDO::PARAM_INT);

    $stmt->execute();

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

  Use LIMIT to paginate data or restrict query results.

  In PDO, bind LIMIT and OFFSET as integers with PDO::PARAM_INT.

  You can combine LIMIT with ORDER BY to get sorted limited results.
