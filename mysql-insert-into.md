# Insert Data into MySQL Table with PHP

## 1. MySQLi Procedural — Simple Insert

```php
<?php
$conn = mysqli_connect("localhost", "root", "your_password", "testdb");
if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
}

$sql = "INSERT INTO users (username, email) VALUES ('Diya', 'diya@example.com')";

if (mysqli_query($conn, $sql)) {
    echo "New record inserted successfully";
} else {
    echo "Error: " . mysqli_error($conn);
}

mysqli_close($conn);
?>
```

---

## 2. MySQLi Procedural — Insert Using Prepared Statement (Safe)

```php
<?php
$conn = mysqli_connect("localhost", "root", "your_password", "testdb");
if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
}

$username = "Diya";
$email = "diya@example.com";

$stmt = mysqli_prepare($conn, "INSERT INTO users (username, email) VALUES (?, ?)");
mysqli_stmt_bind_param($stmt, "ss", $username, $email);

if (mysqli_stmt_execute($stmt)) {
    echo "New record inserted successfully";
} else {
    echo "Error: " . mysqli_error($conn);
}

mysqli_stmt_close($stmt);
mysqli_close($conn);
?>
```

---

## 3. MySQLi OOP — Insert Using Prepared Statement

```php
<?php
$conn = new mysqli("localhost", "root", "your_password", "testdb");
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

$username = "Diya";
$email = "diya@example.com";

$stmt = $conn->prepare("INSERT INTO users (username, email) VALUES (?, ?)");
$stmt->bind_param("ss", $username, $email);

if ($stmt->execute()) {
    echo "New record inserted successfully";
} else {
    echo "Error: " . $conn->error;
}

$stmt->close();
$conn->close();
?>
```

---

## 4. PDO — Simple Insert

```php
<?php
try {
    $conn = new PDO("mysql:host=localhost;dbname=testdb;charset=utf8", "root", "your_password");
    $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

    $sql = "INSERT INTO users (username, email) VALUES ('Diya', 'diya@example.com')";
    $conn->exec($sql);

    echo "New record inserted successfully";

} catch(PDOException $e) {
    echo "Error: " . $e->getMessage();
}
?>
```

---

## 5. PDO — Insert Using Prepared Statements (Recommended)

```php
<?php
try {
    $conn = new PDO("mysql:host=localhost;dbname=testdb;charset=utf8", "root", "your_password");
    $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

    $stmt = $conn->prepare("INSERT INTO users (username, email) VALUES (:username, :email)");
    $stmt->execute([
        ':username' => 'Diya',
        ':email' => 'diya@example.com'
    ]);

    echo "New record inserted successfully";

} catch(PDOException $e) {
    echo "Error: " . $e->getMessage();
}
?>
```

---

## 6. Inserting Multiple Rows with PDO

```php
<?php
try {
    $conn = new PDO("mysql:host=localhost;dbname=testdb;charset=utf8", "root", "your_password");
    $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

    $users = [
        ['username' => 'Alice', 'email' => 'alice@example.com'],
        ['username' => 'Bob', 'email' => 'bob@example.com'],
        ['username' => 'Charlie', 'email' => 'charlie@example.com']
    ];

    $stmt = $conn->prepare("INSERT INTO users (username, email) VALUES (:username, :email)");

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

  Always use prepared statements to avoid SQL injection.

  Replace "your_password" and "testdb" with your actual MySQL password and database.

  Use try-catch with PDO for proper error handling.
