# Insert Multiple Rows with Prepared Statements in PHP & MySQL

## 1. MySQLi Procedural — Insert Multiple Rows with Prepared Statement

```php
<?php
$conn = mysqli_connect("localhost", "root", "your_password", "testdb");
if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
}

$stmt = mysqli_prepare($conn, "INSERT INTO users (username, email) VALUES (?, ?)");
if (!$stmt) {
    die("Prepare failed: " . mysqli_error($conn));
}

$users = [
    ['Diya', 'diya@example.com'],
    ['Alice', 'alice@example.com'],
    ['Bob', 'bob@example.com']
];

foreach ($users as $user) {
    mysqli_stmt_bind_param($stmt, "ss", $user[0], $user[1]);
    if (!mysqli_stmt_execute($stmt)) {
        echo "Error inserting " . $user[0] . ": " . mysqli_stmt_error($stmt) . "<br>";
    }
}

echo "Multiple records inserted successfully";

mysqli_stmt_close($stmt);
mysqli_close($conn);
?>
```

---

## 2. MySQLi Object-Oriented — Insert Multiple Rows with Prepared Statement

```php
<?php
$conn = new mysqli("localhost", "root", "your_password", "testdb");
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

$stmt = $conn->prepare("INSERT INTO users (username, email) VALUES (?, ?)");
if (!$stmt) {
    die("Prepare failed: " . $conn->error);
}

$users = [
    ['Diya', 'diya@example.com'],
    ['Alice', 'alice@example.com'],
    ['Bob', 'bob@example.com']
];

foreach ($users as $user) {
    $stmt->bind_param("ss", $user[0], $user[1]);
    if (!$stmt->execute()) {
        echo "Error inserting " . $user[0] . ": " . $stmt->error . "<br>";
    }
}

echo "Multiple records inserted successfully";

$stmt->close();
$conn->close();
?>
```

---

## 3. PDO — Insert Multiple Rows with Prepared Statement

```php
<?php
try {
    $conn = new PDO("mysql:host=localhost;dbname=testdb;charset=utf8", "root", "your_password");
    $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

    $sql = "INSERT INTO users (username, email) VALUES (:username, :email)";
    $stmt = $conn->prepare($sql);

    $users = [
        ['username' => 'Diya', 'email' => 'diya@example.com'],
        ['username' => 'Alice', 'email' => 'alice@example.com'],
        ['username' => 'Bob', 'email' => 'bob@example.com']
    ];

    foreach ($users as $user) {
        $stmt->execute([
            ':username' => $user['username'],
            ':email' => $user['email']
        ]);
    }

    echo "Multiple records inserted successfully";

} catch(PDOException $e) {
    echo "Error: " . $e->getMessage();
}
?>
```

### Notes:

  Use prepared statements to prevent SQL injection and improve security.

  Replace "your_password" and "testdb" with your actual MySQL password and database name.

  If you want to insert a large number of rows, you can also consider batch inserts (multi-value INSERT) for performance.
