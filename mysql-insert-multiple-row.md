# Insert Multiple Rows into MySQL with PHP

## 1. MySQLi Procedural — Insert Multiple Rows in One Query

```php
<?php
$conn = mysqli_connect("localhost", "root", "your_password", "testdb");
if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
}

$sql = "INSERT INTO users (username, email) VALUES 
    ('Alice', 'alice@example.com'),
    ('Bob', 'bob@example.com'),
    ('Charlie', 'charlie@example.com')";

if (mysqli_query($conn, $sql)) {
    echo "Multiple records inserted successfully";
} else {
    echo "Error: " . mysqli_error($conn);
}

mysqli_close($conn);
?>
```

---

## 2. MySQLi OOP — Insert Multiple Rows Using Loop with Prepared Statement

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

$data = [
    ['Alice', 'alice@example.com'],
    ['Bob', 'bob@example.com'],
    ['Charlie', 'charlie@example.com']
];

foreach ($data as $row) {
    $stmt->bind_param("ss", $row[0], $row[1]);
    $stmt->execute();
}

echo "Multiple records inserted successfully";

$stmt->close();
$conn->close();
?>
```

---

## 3. PDO — Insert Multiple Rows Using Loop with Prepared Statement

```php
<?php
try {
    $conn = new PDO("mysql:host=localhost;dbname=testdb;charset=utf8", "root", "your_password");
    $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

    $stmt = $conn->prepare("INSERT INTO users (username, email) VALUES (:username, :email)");

    $data = [
        ['username' => 'Alice', 'email' => 'alice@example.com'],
        ['username' => 'Bob', 'email' => 'bob@example.com'],
        ['username' => 'Charlie', 'email' => 'charlie@example.com']
    ];

    foreach ($data as $row) {
        $stmt->execute([
            ':username' => $row['username'],
            ':email' => $row['email']
        ]);
    }

    echo "Multiple records inserted successfully";

} catch(PDOException $e) {
    echo "Error: " . $e->getMessage();
}
?>
```

---

## 4. PDO — Insert Multiple Rows in Single Query (Dynamic SQL)

```php
<?php
try {
    $conn = new PDO("mysql:host=localhost;dbname=testdb;charset=utf8", "root", "your_password");
    $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

    $data = [
        ['Alice', 'alice@example.com'],
        ['Bob', 'bob@example.com'],
        ['Charlie', 'charlie@example.com']
    ];

    // Build placeholders
    $placeholders = [];
    $params = [];
    foreach ($data as $index => $row) {
        $placeholders[] = "(?, ?)";
        $params[] = $row[0]; // username
        $params[] = $row[1]; // email
    }

    $sql = "INSERT INTO users (username, email) VALUES " . implode(", ", $placeholders);
    $stmt = $conn->prepare($sql);
    $stmt->execute($params);

    echo "Multiple records inserted successfully in one query";

} catch(PDOException $e) {
    echo "Error: " . $e->getMessage();
}
?>
```

---

## 5. MySQLi — Bulk Insert with Transaction (Safe and Faster)

```php
<?php
$conn = new mysqli("localhost", "root", "your_password", "testdb");
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

$conn->autocommit(FALSE);

$stmt = $conn->prepare("INSERT INTO users (username, email) VALUES (?, ?)");
if (!$stmt) {
    die("Prepare failed: " . $conn->error);
}

$data = [
    ['Alice', 'alice@example.com'],
    ['Bob', 'bob@example.com'],
    ['Charlie', 'charlie@example.com']
];

try {
    foreach ($data as $row) {
        $stmt->bind_param("ss", $row[0], $row[1]);
        $stmt->execute();
    }
    $conn->commit();
    echo "Multiple records inserted successfully within transaction";

} catch (Exception $e) {
    $conn->rollback();
    echo "Failed to insert records: " . $e->getMessage();
}

$stmt->close();
$conn->autocommit(TRUE);
$conn->close();
?>
```
