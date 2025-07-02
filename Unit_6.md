### Handling Strings in Java
Strings in Java are objects that represent sequences of characters. The `String` class is part of the `java.lang` package.

### Creation of Strings
Ways to Create Strings:

**Using String Literal:**

``` java
String str = "Hello";

```

Using `new` Keyword:
``` java
String str = new String("Hello");
```

- String literals are stored in the String Constant Pool.

- Strings are immutable (cannot be changed after creation).

### Concatenation and Conversion of a String
**Concatenation:**
Joining two or more strings using `+` operator or `concat()` method.
``` java
String first = "Hello";
String second = "World";
String result = first + " " + second;
System.out.println(result); // Output: Hello World
```
### Conversion of Other Types to String:
Using `String.valueOf()` or automatic conversion with `+` operator.

``` java
int num = 100;
String str = String.valueOf(num);
System.out.println(str); // Output: 100
```

### Changing Case
Java provides methods to change the case of a string:

``` java
String str = "Java";
System.out.println(str.toUpperCase()); // Output: JAVA
System.out.println(str.toLowerCase()); // Output: java
```

### Character Extraction
Extract a character from a string using charAt() method.
``` java
String str = "Java";
char ch = str.charAt(2); 
System.out.println(ch); // Output: v
```

### String Comparison
Using `equals()` method:
Compares content of strings.
``` java
String s1 = "Java";
String s2 = "Java";
System.out.println(s1.equals(s2)); // Output: true
```
### Using `equalsIgnoreCase()` method:
Ignores case while comparing.
``` java
String s1 = "Java";
String s2 = "java";
System.out.println(s1.equalsIgnoreCase(s2)); // Output: true
```
### Using `compareTo()` method:
Compares two strings lexicographically.
``` java
String s1 = "Apple";
String s2 = "Banana";
System.out.println(s1.compareTo(s2)); // Output: Negative value (because Apple < Banana)
```

### Searching Strings
Using `indexOf()` method:
Finds the first occurrence of a character or substring.
``` java
String str = "Programming";
System.out.println(str.indexOf('g')); // Output: 3
```

### Using `contains()` method:
Checks if a string contains a substring.
``` java
System.out.println(str.contains("gram")); // Output: true
```
### Modifying Strings
**Replace Characters or Substrings:**
``` java
String str = "Java is fun";
String modified = str.replace("fun", "awesome");
System.out.println(modified); // Output: Java is awesome
```
**Substring Extraction:**
``` java
String str = "Hello World";
String sub = str.substring(6);
System.out.println(sub); // Output: World
```
### Cleaning up using the finally clause
Although `finally` is typically used for resource cleanup (e.g., closing files), in string operations, `finally` can be used to ensure certain messages or operations run regardless of exceptions.

``` java
public class Example {
    public static void main(String[] args) {
        try {
            String str = null;
            System.out.println(str.length());  // NullPointerException
        } catch (Exception e) {
            System.out.println("Exception occurred: " + e);
        } finally {
            System.out.println("String operation completed (cleanup in finally).");
        }
    }
}
```

