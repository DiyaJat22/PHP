# Create MySQL Database with PHP

## 1. Using MySQLi (Procedural style)

```php
<?php
$servername = "localhost";
$username = "root";
$password = "your_password";

// Create connection
$conn = mysqli_connect($servername, $username, $password);

// Check connection
if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
}

// Create database
$sql = "CREATE DATABASE testdb";

if (mysqli_query($conn, $sql)) {
    echo "Database created successfully";
} else {
    echo "Error creating database: " . mysqli_error($conn);
}

// Close connection
mysqli_close($conn);
?>
```

---

## 2. Using MySQLi (Object-Oriented style)

```php
<?php
$servername = "localhost";
$username = "root";
$password = "your_password";

// Create connection
$conn = new mysqli($servername, $username, $password);

// Check connection
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

// Create database
$sql = "CREATE DATABASE sampledb";

if ($conn->query($sql) === TRUE) {
    echo "Database created successfully";
} else {
    echo "Error creating database: " . $conn->error;
}

// Close connection
$conn->close();
?>
```

---

## 3. Using PDO

```php
<?php
$servername = "localhost";
$username = "root";
$password = "your_password";

try {
    $conn = new PDO("mysql:host=$servername", $username, $password);
    // Set PDO error mode to exception
    $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

    // Create database
    $sql = "CREATE DATABASE exampledb";
    $conn->exec($sql);

    echo "Database created successfully";

} catch(PDOException $e) {
    echo "Error creating database: " . $e->getMessage();
}

// Close connection (optional, done automatically at script end)
$conn = null;
?>
```

### Notes:

  Replace "your_password" with your actual MySQL user password.

  Make sure your MySQL user has privileges to create databases.

  These scripts connect to MySQL without specifying a database since the database doesn’t exist yet.
