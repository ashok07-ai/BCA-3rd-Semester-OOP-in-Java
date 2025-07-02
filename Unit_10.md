# Arrays and Collection Classes/Interfaces in Java

### Arrays in Java
Arrays are fixed-size, homogeneous data structures used to store multiple values of the same type.

```java
int[] numbers = {10, 20, 30, 40};
System.out.println(numbers[0]);  // Output: 10
```
**Limitations of Arrays:**
- Fixed size
- Cannot store heterogeneous data
- No built-in methods for easy manipulation

Collections overcome these limitations.

### Collections Framework Overview
The Collections Framework provides ready-made classes and interfaces to store and manipulate groups of objects.

#### Core Interfaces
| Interface  | Description  | 
|------------|-------|
| `List`   | Ordered collection, allows duplicates  | 
| `Set`  | Unordered collection, no duplicates | 
| `Map`    | Key-value pairs, keys unique |

### List Interface
An **ordered** collection that allows duplicate elements.

**Common Implementations:**
1. **ArrayList**: 
Dynamic array, fast for retrieval.

```java
import java.util.ArrayList;

ArrayList<String> list = new ArrayList<>();
list.add("A");
list.add("B");
System.out.println(list);  // Output: [A, B]
```
2. **LinkedList**: 
Doubly-linked list, efficient for insertion and deletion.
```java
import java.util.LinkedList;

LinkedList<String> list = new LinkedList<>();
list.add("X");
list.add("Y");
System.out.println(list);  // Output: [X, Y]
```
3. **Set Interface**
A collection that contains no duplicate elements.

**Common Implementations:**
1. **Hashset**: Unordered, unique elements, based on hashing.

```java
import java.util.HashSet;

HashSet<String> set = new HashSet<>();
set.add("A");
set.add("B");
set.add("A");
System.out.println(set);  // Output: [A, B]
```
2. **TreeSet**: Sorted set, no duplicates, maintains ascending order.
```java 
import java.util.TreeSet;

TreeSet<Integer> set = new TreeSet<>();
set.add(20);
set.add(10);
set.add(30);
System.out.println(set);  // Output: [10, 20, 30]
```

### Map Interface
A collection of key-value pairs, keys are unique.

**Common Implementation:**
1. **Hashmap**
```java
import java.util.HashMap;

HashMap<Integer, String> map = new HashMap<>();
map.put(1, "One");
map.put(2, "Two");
System.out.println(map.get(1));  // Output: One
```
### Accessing Collections/Use of an Iterator
Iterator allows sequential access to collection elements.
``` java
import java.util.*;

ArrayList<String> list = new ArrayList<>();
list.add("A");
list.add("B");

Iterator<String> it = list.iterator();
while (it.hasNext()) {
    System.out.println(it.next());
}
```
### Comparator Interface
Used to define custom sorting for objects.
```java 
import java.util.*;

class Student {
    String name;
    int marks;

    Student(String name, int marks) {
        this.name = name;
        this.marks = marks;
    }
}

class SortByMarks implements Comparator<Student> {
    public int compare(Student a, Student b) {
        return a.marks - b.marks;
    }
}

public class Example {
    public static void main(String[] args) {
        ArrayList<Student> list = new ArrayList<>();
        list.add(new Student("John", 50));
        list.add(new Student("Alice", 70));

        Collections.sort(list, new SortByMarks());

        for (Student s : list) {
            System.out.println(s.name + " - " + s.marks);
        }
    }
}
```



