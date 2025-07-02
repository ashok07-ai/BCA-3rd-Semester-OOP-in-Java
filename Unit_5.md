### Exception Handling in Java
### Basic Exceptions
An exception is an unwanted or unexpected event that disrupts the normal flow of a program.
- Java provides a powerful mechanism to handle such situations using exceptions.
- All exceptions are objects derived from the Throwable class.

**Common Built-in Exceptions:**
- `ArithmeticException` → Division by zero
- `NullPointerException` → Accessing object with null reference
- `ArrayIndexOutOfBoundsException` → Accessing invalid array index
- `NumberFormatException` → Invalid conversion of string to number

``` java
public class Example {
    public static void main(String[] args) {
        int a = 10, b = 0;
        int result = a / b;  // Causes ArithmeticException
        System.out.println(result);
    }
}
```

### Proper Use of Exceptions
- Exceptions help separate error handling from normal code logic.
- Should be used for unexpected situations only, not normal control flow.
- Improves program reliability and readability.

**Best Practices:**
- Use specific exception types.
- Catch exceptions at the right place.
- Use finally to clean up resources.
- Don't swallow exceptions silently.

### User-Defined (Custom) Exceptions
You can create your own exception by extending the Exception class.

``` java
class InvalidAgeException extends Exception {
    public InvalidAgeException(String message) {
        super(message);
    }
}

public class Test {
    static void checkAge(int age) throws InvalidAgeException {
        if (age < 18)
            throw new InvalidAgeException("Age must be 18 or above");
    }

    public static void main(String[] args) {
        try {
            checkAge(16);
        } catch (InvalidAgeException e) {
            System.out.println("Exception caught: " + e.getMessage());
        }
    }
}
```

### Catching Exceptions
Catching exceptions prevents program termination.

- Done using `try-catch `blocks.
- Multiple `catch` blocks can be used for different exceptions.

``` java
public class Example {
    public static void main(String[] args) {
        try {
            int arr[] = {1, 2, 3};
            System.out.println(arr[5]);
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Exception caught: " + e);
        }
    }
}
```

### try, catch, Throwing and Re-throwing, finally
- `try-catch` **Block**:
- `try`: Wraps code that might throw an exception.
- `catch`: Handles the exception if it occurs.

`throw` Keyword:
- Used to explicitly throw an exception.

``` java
throw new ArithmeticException("Divide by zero error");
```
`throws` Keyword:
- Declares that a method may throw an exception.
``` java
void riskyMethod() throws IOException {
    // code
}
```
### Re-throwing an Exception:
You can catch an exception and re-throw it to be handled elsewhere.
``` java
try {
    throw new ArithmeticException("Error occurred");
} catch (ArithmeticException e) {
    System.out.println("Handling and re-throwing");
    throw e;
}
```

`finally` Block:
- Always executes whether an exception occurs or not.
- Used for cleanup tasks like closing files, releasing resources, etc.

``` java
try {
    int a = 5 / 0;
} catch (ArithmeticException e) {
    System.out.println("Exception caught");
} finally {
    System.out.println("Cleanup done in finally block");
}

```