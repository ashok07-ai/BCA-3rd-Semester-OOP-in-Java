# File Handling & Streams in Java (`java.io` Package)
**java.io Package**
The `java.io` package provides classes for input and output operations such as:
- Reading and writing files
- Handling console input/output
- Working with byte and character streams
- Serialization

**Files and Directories** <br>
The `File` class is used to represent files and directories.

```java
import java.io.File;

public class Example {
    public static void main(String[] args) {
        File file = new File("example.txt");

        if (file.exists()) {
            System.out.println("File exists");
        } else {
            System.out.println("File does not exist");
        }
    }
}
```

**Common File Methods:**
| Method  | Description  | 
|------------|-------|
| `exists()`   | Checks if file/directory exists  | 
| `createNewFile()`  | Creates a new file | 
| `delete()`    | Deletes file/directory |
| `length()`  | Returns size of file (bytes) | 

### Streams
A Stream is a sequence of data. Java has two types of streams:

**Byte Streams (InputStream, OutputStream)**
Used to perform input/output of raw binary data.<br>
**Example** (FileInputStream, FileOutputStream):

``` java
import java.io.*;

public class ByteStreamExample {
    public static void main(String[] args) throws IOException {
        FileOutputStream out = new FileOutputStream("output.txt");
        out.write(65);  // Writes 'A'
        out.close();

        FileInputStream in = new FileInputStream("output.txt");
        int i = in.read();
        System.out.println((char)i);  // Output: A
        in.close();
    }
}
```
### Character Streams (`Reader`, `Writer`)
Used to perform input/output of character data. <br>
**Example** (FileReader, FileWriter):
``` java
import java.io.*;

public class CharStreamExample {
    public static void main(String[] args) throws IOException {
        FileWriter writer = new FileWriter("output.txt");
        writer.write("Hello World");
        writer.close();

        FileReader reader = new FileReader("output.txt");
        int ch;
        while ((ch = reader.read()) != -1) {
            System.out.print((char) ch);
        }
        reader.close();
    }
}
```
### Reading/Writing Console Input/Output
Using `BufferedReader` for console input:
```java
import java.io.*;

public class ConsoleInput {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        System.out.print("Enter name: ");
        String name = br.readLine();
        System.out.println("Hello " + name);
    }
}
```
### Reading and Writing Files
Using `BufferedReader` and `BufferedWriter`:
```java 
import java.io.*;

public class FileReadWrite {
    public static void main(String[] args) throws IOException {
        BufferedWriter writer = new BufferedWriter(new FileWriter("file.txt"));
        writer.write("This is a file.");
        writer.close();

        BufferedReader reader = new BufferedReader(new FileReader("file.txt"));
        String line;
        while ((line = reader.readLine()) != null) {
            System.out.println(line);
        }
        reader.close();
    }
}
```
### The Serialization Interface
Serialization is the process of converting an object into a byte stream for storage or transmission.
- A class must implement the `Serializable` interface.
- The object can then be saved to a file or sent over a network.

### Serialization and Deserialization
**Serialization (Saving Object to File):**
``` java
import java.io.*;

class Student implements Serializable {
    int id;
    String name;
    
    Student(int id, String name) {
        this.id = id;
        this.name = name;
    }
}

public class SerializeExample {
    public static void main(String[] args) throws IOException {
        Student s = new Student(1, "John");

        ObjectOutputStream out = new ObjectOutputStream(new FileOutputStream("student.ser"));
        out.writeObject(s);
        out.close();
        System.out.println("Object Serialized");
    }
}
```
**Deserialization (Reading Object from File):**
``` java
import java.io.*;

public class DeserializeExample {
    public static void main(String[] args) throws IOException, ClassNotFoundException {
        ObjectInputStream in = new ObjectInputStream(new FileInputStream("student.ser"));
        Student s = (Student) in.readObject();
        in.close();

        System.out.println("ID: " + s.id + ", Name: " + s.name);
    }
}
```
