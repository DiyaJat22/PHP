# PHP Loops

## 🔁 **Loops in PHP**

Loops in PHP are used to execute a block of code **repeatedly** as long as a specified condition is true. They help reduce redundancy and make the code more efficient and readable.

---

### 🔹 1. `while` Loop

- **Syntax**:
    
    ```php
    php
    CopyEdit
    while (condition) {
        // Code to execute
    }
    
    ```
    
- **Description**: Executes the block **as long as the condition is true**.
- **Use Case**: When the number of iterations is **not known in advance**.

---

### 🔹 2. `do...while` Loop

- **Syntax**:
    
    ```php
    php
    CopyEdit
    do {
        // Code to execute
    } while (condition);
    
    ```
    
- **Description**: Executes the block **at least once**, and then continues if the condition is true.
- **Use Case**: When you want the loop to run **at least one time**, even if the condition is false.

---

### 🔹 3. `for` Loop

- **Syntax**:
    
    ```php
    php
    CopyEdit
    for (initialization; condition; increment/decrement) {
        // Code to execute
    }
    
    ```
    
- **Description**: Best for loops with a **fixed number of iterations**.
- **Use Case**: When you know exactly how many times to loop.

---

### 🔹 4. `foreach` Loop

- **Syntax**:
    
    ```php
    php
    CopyEdit
    foreach ($array as $value) {
        // Code to execute
    }
    
    foreach ($array as $key => $value) {
        // Code to execute
    }
    
    ```
    
- **Description**: Specifically used to loop through **arrays**.
- **Use Case**: When working with associative or indexed arrays.

---

## 🔸 Loop Control Statements

1. **`break`**: Exits the loop entirely.
2. **`continue`**: Skips the current iteration and continues with the next.

---

# PHP Loops Summary

| Loop Type        | Description | Syntax Example | Use Case |
|------------------|-------------|----------------|----------|
| **for**          | Loops through a block of code a specified number of times. | ```php<br>for ($i = 0; $i < 5; $i++) {<br>    echo $i;<br>}<br>``` | When the number of iterations is known in advance. |
| **while**        | Loops through a block of code as long as the specified condition is true. | ```php<br>$i = 0;<br>while ($i < 5) {<br>    echo $i;<br>    $i++;<br>}<br>``` | When you don't know how many times the loop should run beforehand. |
| **do...while**   | Executes the block of code once, then repeats as long as the condition is true. | ```php<br>$i = 0;<br>do {<br>    echo $i;<br>    $i++;<br>} while ($i < 5);<br>``` | When the code should run at least once regardless of the condition. |
| **foreach**      | Loops through each element in an array or object. | ```php<br>$arr = [1, 2, 3];<br>foreach ($arr as $value) {<br>    echo $value;<br>}<br>``` | When iterating over arrays or collections. |

