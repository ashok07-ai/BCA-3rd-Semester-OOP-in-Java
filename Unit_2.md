# Tokens, Expressions and Control Structures

## Tokens, Expressions, and Control Structures
### Tokens
Tokens are the smallest individual elements in a Java program. They include:
- **Keywords**: Reserved words like `int`, `class`, `public`, etc.
- **Identifiers**: Names given to variables, methods, classes, etc.
- **Literals**: Constant values like `10`, `3.14`, `'A'`, `true`, etc.
- **Operators**: Symbols like `+`, `-`, `*`, `/`, etc.
- **Separators**: Symbols like `;`, `,`, `{}`, etc.

### Expressions
An expression is a combination of variables, operators, and method calls that evaluates to a single value. Example:
```java
int result = 10 + 5 * 2; // Expression
```

### Control Structures
Control structures determine the flow of execution in a program. They include:
- **Branching:** Branching allows the program to make decisions and execute different blocks of code based on conditions. Example: `if`, `if-else`, `switch`
``` java
if (condition) {
    // Code to execute if the condition is true
} else {
    // Code to execute if the condition is false
}
```

``` java
if (condition){
    // Code to execute if the condition is true
}else if (condition){
    // Code to execute if the condition is false
}else{

}
```

```java 
switch (variable) {
    case value1:
        // Code to execute if variable == value1
        break;
    case value2:
        // Code to execute if variable == value2
        break;
    default:
        // Code to execute if variable doesn't match any case
        break;
}
```


- **Looping:** Looping allows the program to repeat a block of code multiple times. Example: `while`, `do-while`, `for`
``` java
while (condition) {
    // Code to execute while the condition is true
}
```

``` java
do {
    // Code to execute at least once
} while (condition);
```

``` java
for (initialization; condition; update) {
    // Code to execute for each iteration
}
```

- **Jumping:** Jumping allows the program to alter the flow of execution by jumping to a different part of the code. Example: `break`, `continue`, `return`
``` java
// Used to exit a loop or switch statement
break;
```

``` java
// Used to skip the rest of the current iteration and move to the next iteration of the loop
continue;
```

``` java
// Used to exit a function and optionally return a value
return value;
```

### Example Java Code Combining All Structures
``` java
public class ControlStructuresExample {

    // Function to calculate grade based on score
    public static String calculateGrade(int score) {
        if (score >= 90) {
            return "A";
        } else if (score >= 80) {
            return "B";
        } else if (score >= 70) {
            return "C";
        } else {
            return "F";
        }
    }

    // Function to print numbers up to n, skipping 5
    public static void printNumbersUpTo(int n) {
        for (int i = 1; i <= n; i++) {
            if (i == 5) {
                continue; // Skip printing 5
            }
            System.out.println(i);
        }
    }

    // Function to find the first negative number in an array
    public static void findFirstNegative(int[] numbers) {
        for (int num : numbers) {
            if (num < 0) {
                System.out.println("First negative number found: " + num);
                break; // Exit the loop
            }
        }
    }

    public static void main(String[] args) {
        // Example usage
        System.out.println("Grade for score 85: " + calculateGrade(85));

        System.out.println("Printing numbers up to 10 (skipping 5):");
        printNumbersUpTo(10);

        int[] numbers = {1, 2, -3, 4, -5};
        System.out.println("Finding the first negative number:");
        findFirstNegative(numbers);
    }
}
```

### Datatypes
A data type in Java specifies the type of value a variable can store. It determines the size, memory allocation, and operations that can be performed on the data.

### Types of Datatypes
-**Primitive Datatypes:** Primitive data types are the most basic data types available in Java. They represent simple values and are not objects. Java provides the following primitive data types:

| Data Type  | Size  | Default Value | Example Value  |
|------------|-------|--------------|---------------|
| **byte**   | 1 byte  | `0`   | `127` |
| **short**  | 2 bytes | `0`   | `32000` |
| **int**    | 4 bytes | `0`   | `100000` |
| **long**   | 8 bytes | `0L`  | `1000000000L` |
| **float**  | 4 bytes | `0.0f` | `10.5f` |
| **double** | 8 bytes | `0.0d` | `99.99d` |
| **char**   | 2 bytes | `'\u0000'` | `'A'` |
| **boolean** | 1 bit | `false` | `true` or `false` |

```java
Example of Primitive Datatypes
int age = 25;
double salary = 50000.75;
char grade = 'A';
boolean isJavaFun = true;
```

-**Non Primitive Datatypes/User Defined Datatypes:** 
Non-primitive data types are more complex data types in Java. They are derived from primitive data types and allow the storage of multiple values and more complex operations. These include: 
- **String** → `String name = "Java";`
``` java
public class StringExample {
    public static void main(String[] args) {
        String name = "Java";
        System.out.println("Welcome to " + name);
    }
}
```
- **Arrays** → `int[] numbers = {1, 2, 3};`
``` java
public class ArrayExample {
    public static void main(String[] args) {
        int[] numbers = {1, 2, 3, 4, 5};

        // Loop through array
        for (int num : numbers) {
            System.out.print(num + " ");
        }
    }
}

```
- **Classes** → `class Car { }`
``` java
class Car {
    String brand;
    int speed;

    // Constructor
    Car(String brand, int speed) {
        this.brand = brand;
        this.speed = speed;
    }

    void display() {
        System.out.println("Car: " + brand + ", Speed: " + speed + " km/h");
    }
}

public class ClassExample {
    public static void main(String[] args) {
        Car myCar = new Car("Toyota", 180);
        myCar.display();
    }
}

```
- **Interfaces** → `interface Vehicle { }`
```java
interface Vehicle {
    void start(); // Abstract method
}

class Bike implements Vehicle {
    public void start() {
        System.out.println("Bike is starting...");
    }
}

public class InterfaceExample {
    public static void main(String[] args) {
        Bike myBike = new Bike();
        myBike.start();
    }
}

```
- **Enums** → `enum Days { MON, TUE, WED };`
```java
enum Days {
    MON, TUE, WED, THU, FRI, SAT, SUN
}

public class EnumExample {
    public static void main(String[] args) {
        Days today = Days.WED;
        System.out.println("Today is: " + today);
    }
}
```

### Declarations, Constants, and Identifiers
- **Declarations:** Defining a variable with a data type.
- **Constants:** Variables whose values cannot change, declared using final.
- **Identifiers:** Names given to variables, methods, classes, etc.
```java
final double PI = 3.14159; // Constant
int count = 10; // Variable declaration
```

### Type Conversion and Casting
- **Type Conversion (Implicit Conversion):** Automatically done by the compiler (e.g., int to double).
- **Type Casting (Explicit Casting):** Manually converting one type to another.

### Comparison between Type Conversion and Type Casting
# Difference between Type Casting and Type Conversion

| Feature               | Type Casting                             | Type Conversion                            |
|-----------------------|------------------------------------------|--------------------------------------------|
| **Definition**         | Explicit conversion of one data type to another by the programmer. | Automatic or implicit conversion done by the compiler. |
| **Method**             | Manual conversion using syntax.          | Automatically handled by the compiler based on rules. |
| **Example**            | `int x = 10; double y = (double) x;`     | `int x = 10; double y = x;`               |
| **Automatic or Manual**| Manual                                   | Automatic                                  |
| **Control**            | The programmer has control over conversion. | The compiler handles the conversion process. |
| **Loss of Data**       | Possible, especially in downcasting.     | Rare, as the compiler ensures data safety. |


```java
double num1 = 10.5;
int num2 = (int) num1; // Explicit casting
```

### Variables   
- **Variable Definition:** Declaring a variable with a data type.
- **Assignment:** Assigning a value to a variable.
- **Default Initialization:** Primitive types have default values (e.g., int defaults to 0).

``` java
int x; // Declaration
x = 10; // Assignment
```

### Command-Line Arguments
Command-line arguments are passed to the main method as an array of strings.

``` java
public class Main {
    public static void main(String[] args) {
        System.out.println("First argument: " + args[0]);
    }
}
```

### Arrays of Primitive Data Types
Arrays are used to store multiple values of the same type.
``` java
int[] numbers = {1, 2, 3, 4, 5};
```

### Comment Syntax
Java supports single-line and multi-line comments.
``` java
// This is a single-line comment

/*
This is a
multi-line comment
*/
```

### Garbage Collection
Java automatically manages memory using garbage collection. Developers do not need to manually free memory.

### Expressions and Operators
In Java, an expression is a combination of variables, constants, operators, and method calls that evaluate to a single value. Operators are symbols that perform operations on operands in an expression.

- **Arithmatic Operators:** Perform basic mathematical operations. Example: `+`, `-`, `*`, `/`, `%`.
```java
public class ArithmeticExample {
    public static void main(String[] args) {
        int a = 10, b = 5;
        System.out.println("Addition: " + (a + b));  // 15
        System.out.println("Subtraction: " + (a - b)); // 5
        System.out.println("Multiplication: " + (a * b)); // 50
        System.out.println("Division: " + (a / b)); // 2
        System.out.println("Modulus: " + (a % b)); // 0
    }
}
```

- **Relational(Comparison) Operators:** Compare two values. Example: `==`, `!=`, `>`, `<`, `>=`, `<=`.
```java
public class ComparisonExample {
    public static void main(String[] args) {
        int x = 10, y = 5;
        System.out.println(x > y);  // true
        System.out.println(x < y);  // false
        System.out.println(x == y); // false
        System.out.println(x != y); // true
    }
}

```


- **Logical Operators:** Perform logical operations. Example: `AND(&&)`, `OR (||)`, `NOT(!)`.
```java
public class LogicalExample {
    public static void main(String[] args) {
        boolean a = true, b = false;
        System.out.println(a && b); // false
        System.out.println(a || b); // true
        System.out.println(!a);     // false
    }
}
```

- **Assignment Operators:** Assign values to variables. Example: `+=`, `-=`, `/=`, `*=`, `=`, `%=`.
```java
public class AssignmentExample {
    public static void main(String[] args) {
        int num = 10;
        num += 5;  // num = num + 5
        System.out.println(num); // 15
    }
}
```

- **Ternary Operator:** Short form of if-else. `condition ? value1 : value2`
```java
public class TernaryExample {
    public static void main(String[] args) {
        int a = 10, b = 5;
        int min = (a < b) ? a : b;
        System.out.println("Smaller number is: " + min); // 5
    }
}
```

- **Bitwise Operators:** Work on bits and perform bit-level operations. `&`, `|`, `^`, `~`
```java
public class BitwiseExample {
    public static void main(String[] args) {
        int a = 5, b = 3; // 5 = 0101, 3 = 0011
        System.out.println("Bitwise AND: " + (a & b)); // 1 (0001)
        System.out.println("Bitwise OR: " + (a | b));  // 7 (0111)
        System.out.println("Bitwise XOR: " + (a ^ b)); // 6 (0110)
        System.out.println("Left Shift: " + (a << 1)); // 10 (1010)
        System.out.println("Right Shift: " + (a >> 1)); // 2 (0010)
    }
}
```

- **Unary Operators(Auto increment, Auto decrement):** Work with a single operand. `+`, `-`, `++`, `--`, `!`
```java
public class UnaryExample {
    public static void main(String[] args) {
        int num = 5;
        System.out.println(num++); // 5 (Post-increment)
        System.out.println(++num); // 7 (Pre-increment)
        System.out.println(--num); // 6 (Pre-decrement)
        System.out.println(num--); // 6 (Post-decrement)
    }
}
```

## **Shift Operators in Java**

Shift operators in Java are used to shift the bits of a number left or right, which effectively multiplies or divides the number by powers of 2.

### **1. Left Shift (`<<`)**
- Moves bits to the left and fills with `0s`.
- Equivalent to multiplication by `2^n`.

```java
public class LeftShiftExample {
    public static void main(String[] args) {
        int num = 5;  // Binary: 00000101
        int result = num << 2;  // Shift left by 2 (5 * 2^2 = 20)

        System.out.println("Left Shift: " + result); // Output: 20
    }
}
```

### **2. Right Shift (`>>`) (Signed)**
- Moves bits to the right and fills with the **sign bit** (`0` for positive, `1` for negative).
- Equivalent to division by `2^n`.

```java
public class RightShiftExample {
    public static void main(String[] args) {
        int num = 20;  // Binary: 00010100
        int result = num >> 2;  // Shift right by 2 (20 / 2^2 = 5)

        System.out.println("Right Shift: " + result); // Output: 5
    }
}
```

### **3. Unsigned Right Shift (`>>>`)**
- Moves bits to the right and fills with `0s`, ignoring the sign bit.
- Used to handle **unsigned values** in Java.

```java
public class UnsignedRightShiftExample {
    public static void main(String[] args) {
        int num = -20;  // Binary: 11101100 (for 8-bit representation)
        int result = num >>> 2;  // Shift right by 2, fill with 0s

        System.out.println("Unsigned Right Shift: " + result);
    }
}
```

### Comparison table
# Bitwise Shift Operators

The following table describes the effects of bitwise shift operators:

| Operator | Description               | Effect                                     |
|----------|---------------------------|--------------------------------------------|
| `<<`     | Left shift                | Multiplies by \(2^n\)                      |
| `>>`     | Right shift (Signed)      | Divides by \(2^n\), keeps the sign bit    |
| `>>>`    | Right shift (Unsigned)    | Divides by \(2^n\), fills with 0s         |
