# Using java.lang and java.util Packages

### Using java.lang Package
The `java.lang` package is automatically imported in every Java program. It contains fundamental classes essential for Java programs.

**`java.lang.Math` Class**
Provides methods for mathematical operations such as square root, power, trigonometry, etc.

#### Common Methods
| Method  | Description  | 
|------------|-------|
| `Math.abs(x)`   | Absolute value  | 
| `ath.sqrt(x)`  | Square root | 
| `Math.pow(x, y)`    | x raised to power y |
| `Math.max(x, y)`  | Maximum of two values | 
| `Math.min(x, y)`  | Minimum of two values | 
| `Math.random()`  | Generates random number [0,1) | 

```java
System.out.println(Math.sqrt(16));   // Output: 4.0
System.out.println(Math.pow(2, 3));  // Output: 8.0
System.out.println(Math.abs(-10));   // Output: 10
```
### Wrapper Classes and Associated Methods
Wrapper classes convert primitive data types into objects.
| Primitive  | Wrapper Class  | 
|------------|-------|
| `byte`   | Byte  | 
| `short`  | Short | 
| `int`    | Integer |
| `long`  | Long | 
| `float`  | Float | 
| `double`  | Double | 
| `char`  | Character | 
| `boolean`  | Boolean | 

### Common Wrapper Methods
```java
int a = Integer.parseInt("100");   // String to int
String s = Integer.toString(100);  // int to String

double d = Double.parseDouble("10.5");  // String to double
boolean b = Boolean.parseBoolean("true");  // String to boolean
```
### Autoboxing and Unboxing
- **Autoboxing**: Automatic conversion of primitive to wrapper class.
- **Unboxing**: Automatic conversion of wrapper to primitive.
``` java
Integer num = 10;  // Autoboxing
int val = num;     // Unboxing
```
Using `java.util` Package
The `java.util` package contains utility classes like collections, random number generators, etc.

**Core Classes**
1. **Vector** <br>
A growable array that can store objects.

```java
import java.util.Vector;

Vector<String> v = new Vector<>();
v.add("A");
v.add("B");
System.out.println(v);  // Output: [A, B]
```
2. **Stack** <br>
A subclass of Vector that implements LIFO (Last In, First Out).

```java
import java.util.Stack;

Stack<Integer> stack = new Stack<>();
stack.push(10);
stack.push(20);
System.out.println(stack.pop());  // Output: 20
```
3. **Dictionary (Abstract Class)** <br>
Superclass for key-value pair data structures like Hashtable.

4. **Hashtable** <br>
Stores key-value pairs. Keys are unique; no null keys allowed.

``` java
import java.util.Hashtable;

Hashtable<Integer, String> ht = new Hashtable<>();
ht.put(1, "One");
ht.put(2, "Two");
System.out.println(ht.get(1));  // Output: One
```
5. **Enumeration** <br>
Used to iterate elements of legacy classes like Vector or Hashtable.
```java
import java.util.*;

Vector<String> v = new Vector<>();
v.add("A");
v.add("B");

Enumeration<String> e = v.elements();
while (e.hasMoreElements()) {
    System.out.println(e.nextElement());
}
```

### Random Number Generation
The `Random` class generates random numbers.
```java 
import java.util.Random;

Random r = new Random();
System.out.println(r.nextInt(100));  // Random number between 0 and 99
System.out.println(r.nextDouble());  // Random double between 0.0 and 1.0
```
