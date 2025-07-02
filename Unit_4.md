# Inheritance & Packaging

### Inheritance
Inheritance allows a class (subclass) to acquire properties and methods of another class (superclass).
- Promotes code reusability.
- Achieved using the `extends` keyword.

``` java
class Animal {
    void eat() {
        System.out.println("This animal eats food.");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Dog barks.");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog d = new Dog();
        d.eat();  // Inherited method
        d.bark(); // Own method
    }
}

```

### Subclasses and Superclasses
- **Superclass**: The parent class whose properties are inherited.
- **Subclass**: The child class that inherits from the superclass.

### `super` Keyword Usage
- Refers to the immediate parent class object.
- Used to call parent class constructor or method.

``` java
class Animal {
    Animal() {
        System.out.println("Animal constructor called");
    }
}

class Dog extends Animal {
    Dog() {
        super();  // Calls Animal constructor
        System.out.println("Dog constructor called");
    }
}
```
### Overriding Methods
Subclass provides a specific implementation for a method already defined in the superclass.

``` java
class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}

```

### Dynamic Method Dispatch (Runtime Polymorphism)
- Deciding which version of a method to execute at runtime, not compile-time.
- Achieved through method overriding and parent class reference pointing to child class object.

``` java 
class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    void sound() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal a = new Dog(); // Parent reference, Child object
        a.sound();  // Calls Dog's version due to dynamic method dispatch
    }
}

```

### The Object Class
- Root class of all Java classes.
- Provides methods like toString(), equals(), hashCode().

### Abstract and Final Classes
**Abstract Class**
- Cannot be instantiated.
- Can have abstract (unimplemented) and concrete methods.

``` java
abstract class Animal {
    abstract void sound();
}
```

**Final Class**
- Cannot be extended (inherited).
```java
final class Animal { }

```
### Packages
**Defining a Package**
Group related classes into a single unit using `package` keyword.

``` java
package mypackage;
public class MyClass { }
```

### Importing a Package
Use `import` to access classes from other packages.
``` java
import mypackage.MyClass;
```

### Access Control in Packages
- **public**: Accessible everywhere.

- **protected**: Accessible within package and subclasses.

- **Default** (no modifier): Accessible within the same package only.

- **private**: Accessible only within the class.

### Interfaces
**Defining an Interface**
- Interface contains only abstract methods (by default).
- Achieves 100% abstraction.
``` java
interface Animal {
    void sound();
}
```

### Implementing and Applying Interfaces
``` java
interface Animal {
    void sound();
}

class Dog implements Animal {
    public void sound() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog d = new Dog();
        d.sound();
    }
}
```



