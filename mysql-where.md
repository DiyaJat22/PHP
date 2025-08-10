# Using WHERE Clause in MySQL SELECT with PHP

## 1. MySQLi Procedural — Simple WHERE Condition

```php
<?php
$conn = mysqli_connect("localhost", "root", "your_password", "testdb");
if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
}

$username = "Diya";
$sql = "SELECT id, username, email FROM users WHERE username = '$username'";
$result = mysqli_query($conn, $sql);

if (mysqli_num_rows($result) > 0) {
    while ($row = mysqli_fetch_assoc($result)) {
        echo "ID: " . $row["id"] . " - Username: " . $row["username"] . " - Email: " . $row["email"] . "<br>";
    }
} else {
    echo "No records found";
}

mysqli_close($conn);
?>
```

  Note: This is vulnerable to SQL injection if $username comes from user input. Use prepared statements instead.

---

## 2. MySQLi Procedural — WHERE with Prepared Statement (Safe)

```php
<?php
$conn = mysqli_connect("localhost", "root", "your_password", "testdb");
if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
}

$username = "Diya";
$stmt = mysqli_prepare($conn, "SELECT id, username, email FROM users WHERE username = ?");
mysqli_stmt_bind_param($stmt, "s", $username);
mysqli_stmt_execute($stmt);

$result = mysqli_stmt_get_result($stmt);
if (mysqli_num_rows($result) > 0) {
    while ($row = mysqli_fetch_assoc($result)) {
        echo "ID: " . $row["id"] . " - Username: " . $row["username"] . " - Email: " . $row["email"] . "<br>";
    }
} else {
    echo "No records found";
}

mysqli_stmt_close($stmt);
mysqli_close($conn);
?>
```

---

## 3. MySQLi OOP — WHERE with Prepared Statement

```php
<?php
$conn = new mysqli("localhost", "root", "your_password", "testdb");
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

$username = "Diya";
$stmt = $conn->prepare("SELECT id, username, email FROM users WHERE username = ?");
$stmt->bind_param("s", $username);
$stmt->execute();

$result = $stmt->get_result();
if ($result->num_rows > 0) {
    while ($row = $result->fetch_assoc()) {
        echo "ID: " . $row["id"] . " - Username: " . $row["username"] . " - Email: " . $row["email"] . "<br>";
    }
} else {
    echo "No records found";
}

$stmt->close();
$conn->close();
?>
```

---

## 4. PDO — WHERE with Prepared Statement

```php
<?php
try {
    $conn = new PDO("mysql:host=localhost;dbname=testdb;charset=utf8", "root", "your_password");
    $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

    $username = "Diya";
    $stmt = $conn->prepare("SELECT id, username, email FROM users WHERE username = :username");
    $stmt->execute([':username' => $username]);

    $user = $stmt->fetchAll(PDO::FETCH_ASSOC);

    if ($user) {
        foreach ($user as $row) {
            echo "ID: " . $row["id"] . " - Username: " . $row["username"] . " - Email: " . $row["email"] . "<br>";
        }
    } else {
        echo "No records found";
    }

} catch(PDOException $e) {
    echo "Error: " . $e->getMessage();
}
?>
```

### Common WHERE Conditions Examples:

  Equal to: WHERE username = 'Diya'

  Not equal: WHERE age <> 30

  Greater than: WHERE salary > 50000

  Less than or equal: WHERE created_at <= '2025-08-01'

  LIKE (pattern matching): WHERE email LIKE '%@example.com'

  IN (list): WHERE id IN (1, 2, 3)

  BETWEEN: WHERE created_at BETWEEN '2025-01-01' AND '2025-06-30'

