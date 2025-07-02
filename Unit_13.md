# Database Programming using JDBC
### What is JDBC?
- JDBC (Java Database Connectivity) is an API that allows Java applications to interact with relational databases like MySQL, Oracle, PostgreSQL, etc.
- It enables performing operations such as inserting, updating, deleting, and retrieving data from a database.

#### Basic Steps for JDBC Database Programming
The lifecycle of an applet is managed by the browser or applet viewer, and consists of the following methods:
| Step  | Description  | 
|------------|-------|
| `1`   | Load the database driver.  | 
| `2`  | Establish a connection to the database. | 
| `3`    | Create a `Statement` or `PreparedStatement`. |
| `4`    | Execute SQL queries using the statement. |
| `5`    | Process the results using `ResultSet`. |
| `6`    | Close the connection. |

### Using `Connection`, `Statement`, and `ResultSet` Interfaces
1. **Loading the Driver**
- For MySQL
``` java
Class.forName("com.mysql.cj.jdbc.Driver");
```
2. **Establishing Connection**
```java
import java.sql.*;

Connection con = DriverManager.getConnection(
    "jdbc:mysql://localhost:3306/testdb", "root", "password"
);
System.out.println("Connected Successfully");
```
3. **Creating a Statement**
```java
Statement stmt = con.createStatement();
```
4. **Executing SQL Queries**
- **Insert/Update/Delete Operations**
```java 
int rows = stmt.executeUpdate("INSERT INTO student (id, name) VALUES (1, 'John')");
System.out.println(rows + " record(s) inserted");
````
- **Retrieving Data (SELECT Query)**
```java 
ResultSet rs = stmt.executeQuery("SELECT * FROM student");

while (rs.next()) {
    int id = rs.getInt("id");
    String name = rs.getString("name");
    System.out.println(id + " - " + name);
}
```
### Closing the Connection
```java
rs.close();
stmt.close();
con.close();
```

### Summary of Important Interfaces
| Interface  | Description  | 
|------------|-------|
| `DriverManager`   | Manages JDBC drivers and connections.  | 
| `Connection`  | Represents a connection to the database. | 
| `Statement`    | Used to execute static SQL queries. |
| `PreparedStatement`    | Used for dynamic, parameterized SQL queries (recommended). |
| `ResultSet`    | Holds the result of a SELECT query. |

### Using `PreparedStatement` (Best Practice)
Helps prevent SQL Injection and handles dynamic data efficiently.
```java 
String sql = "INSERT INTO student (id, name) VALUES (?, ?)";
PreparedStatement ps = con.prepareStatement(sql);
ps.setInt(1, 2);
ps.setString(2, "Alice");
ps.executeUpdate();
```
### Exception Handling with JDBC
Always use `try-catch` to handle `SQLException`.
```java 
try {
    // JDBC code
} catch (SQLException e) {
    e.printStackTrace();
}
```

