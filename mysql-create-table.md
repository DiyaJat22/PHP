# Create Table with PHP & MySQL

## 1. MySQLi Procedural - Create Simple Table

```php
<?php
$servername = "localhost";
$username = "root";
$password = "your_password";
$dbname = "testdb";

// Connect to database
$conn = mysqli_connect($servername, $username, $password, $dbname);
if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
}

// SQL to create table
$sql = "CREATE TABLE users (
    id INT(6) UNSIGNED AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) NOT NULL UNIQUE,
    email VARCHAR(50) NOT NULL,
    reg_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP
)";

if (mysqli_query($conn, $sql)) {
    echo "Table users created successfully";
} else {
    echo "Error creating table: " . mysqli_error($conn);
}

mysqli_close($conn);
?>
```

---

## 2. MySQLi Object-Oriented - Create Table with Foreign Key

```php
<?php
$servername = "localhost";
$username = "root";
$password = "your_password";
$dbname = "testdb";

$conn = new mysqli($servername, $username, $password, $dbname);
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

$sql = "CREATE TABLE orders (
    order_id INT(10) UNSIGNED AUTO_INCREMENT PRIMARY KEY,
    user_id INT(6) UNSIGNED,
    product VARCHAR(100) NOT NULL,
    order_date DATETIME DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE CASCADE
)";

if ($conn->query($sql) === TRUE) {
    echo "Table orders created successfully";
} else {
    echo "Error creating table: " . $conn->error;
}

$conn->close();
?>
```

---

## 3. PDO - Create Table with Composite Primary Key

```php
<?php
$servername = "localhost";
$username = "root";
$password = "your_password";
$dbname = "testdb";

try {
    $conn = new PDO("mysql:host=$servername;dbname=$dbname;charset=utf8", $username, $password);
    $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

    $sql = "CREATE TABLE user_roles (
        user_id INT(6) UNSIGNED NOT NULL,
        role_id INT(6) UNSIGNED NOT NULL,
        assigned_date DATE NOT NULL,
        PRIMARY KEY (user_id, role_id)
    )";

    $conn->exec($sql);
    echo "Table user_roles created successfully";

} catch(PDOException $e) {
    echo "Error creating table: " . $e->getMessage();
}
?>
```

---

## 4. MySQLi Procedural - Create Table with ENUM and DEFAULT

```php
<?php
$conn = mysqli_connect("localhost", "root", "your_password", "testdb");
if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
}

$sql = "CREATE TABLE products (
    product_id INT AUTO_INCREMENT PRIMARY KEY,
    product_name VARCHAR(100) NOT NULL,
    status ENUM('in_stock', 'out_of_stock', 'discontinued') DEFAULT 'in_stock',
    price DECIMAL(10,2) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
)";

if (mysqli_query($conn, $sql)) {
    echo "Table products created successfully";
} else {
    echo "Error creating table: " . mysqli_error($conn);
}

mysqli_close($conn);
?>
```

---

## 5. PDO - Create Table with CHECK Constraint (MySQL 8+)

```php
<?php
try {
    $conn = new PDO("mysql:host=localhost;dbname=testdb;charset=utf8", "root", "your_password");
    $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

    $sql = "CREATE TABLE employees (
        emp_id INT AUTO_INCREMENT PRIMARY KEY,
        emp_name VARCHAR(100) NOT NULL,
        salary DECIMAL(10,2) NOT NULL CHECK (salary >= 0),
        hire_date DATE NOT NULL
    )";

    $conn->exec($sql);
    echo "Table employees created successfully";

} catch(PDOException $e) {
    echo "Error creating table: " . $e->getMessage();
}
?>
```

### Notes:

  Replace "your_password" and "testdb" with your actual MySQL password and database name.

  Make sure the database exists before running these scripts.

  The examples cover common data types, constraints, foreign keys, composite keys, enums, defaults, and checks.

  CHECK constraints require MySQL 8.0 or higher.
