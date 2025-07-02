# Object Oriented Programming Concepts

### Fundamental of Classes
A class is a blueprint for creating objects. It defines properties (attributes) and behaviors (methods) that the objects created from the class will have.
- A class encapsulates data and functions into a single unit.
``` java
class Car {
    String color;
    String model;
}

```

### Creating Class Instances
An instance is an object created from a class using the `new` keyword.

``` java
class Car {
    String color;
    String model;

    public static void main(String[] args) {
        Car myCar = new Car(); // Creating an instance
        myCar.color = "Red";
        myCar.model = "Toyota";
        System.out.println("Car Color: " + myCar.color + ", Model: " + myCar.model);
    }
}
```
### Adding Methods to a class
Methods define the behavior of a class and can perform operations on the class data.

``` java
class Car {
    String color;
    String model;

    void display() {
        System.out.println("Car Color: " + color + ", Model: " + model);
    }

    public static void main(String[] args) {
        Car myCar = new Car();
        myCar.color = "Blue";
        myCar.model = "Honda";
        myCar.display();
    }
}
```

### Calling Functions/Methods
Methods are called using the object reference followed by the method name.
```java
Car myCar = new Car();
myCar.display();

```

### Abstraction
Abstraction is the process of hiding complex implementation details and showing only the essential features.
- Achieved using `abstract classes` or `interfaces`.

``` java
abstract class Vehicle {
    abstract void start();
}

```

### Encapsulation
Encapsulation binds data and methods together and restricts direct access to some of an object's components.
-  Achieved by making variables `private` and providing `public` getter/setter methods..


``` java
class Car {
    private String color;

    public void setColor(String color) {
        this.color = color;
    }

    public String getColor() {
        return color;
    }

    public static void main(String[] args) {
        Car myCar = new Car();
        myCar.setColor("Green");
        System.out.println("Car Color: " + myCar.getColor());
    }
}
```

### Using `this` Keyword
The `this` keyword refers to the current object and is used to differentiate instance variables from parameters.

``` java
class Car {
    String color;

    void setColor(String color) {
        this.color = color;
    }

    public static void main(String[] args) {
        Car myCar = new Car();
        myCar.setColor("Yellow");
        System.out.println("Car Color: " + myCar.color);
    }
}
```
### Constructors
Constructors are special methods used to initialize objects. It is automatically called when an instance/object is created

### Types of Constructors
**Default Constructor**
``` java
class Car {
    String color;

    Car() {
        color = "Black";
    }

    public static void main(String[] args) {
        Car myCar = new Car();
        System.out.println("Car Color: " + myCar.color);
    }
}
```

**Parameterized Constructor**
``` java
class Car {
    String color;

    Car(String color) {
        this.color = color;
    }

    public static void main(String[] args) {
        Car myCar = new Car("White");
        System.out.println("Car Color: " + myCar.color);
    }
}
```

### More on Methods
Methods can be overloaded or have parameters passed by value of reference.

**Passing By Value**
In Java, primitive types are passed by value, meaning changes inside the method don't affect the original value.
``` java
class Car {
    int speed;

    void changeSpeed(int speed) {
        speed = speed; // No change to original value
    }

    public static void main(String[] args) {
        Car myCar = new Car();
        myCar.speed = 60;
        myCar.changeSpeed(100);
        System.out.println("Speed: " + myCar.speed); // Still 60
    }
}
```

**Passing by Reference (for Objects)**
For objects, the reference (memory address) is passed by value. Changes to the object's properties inside the method affect the original object.
``` java
class Car {
    String color;

    // Method to display car color
    void displayColor() {
        System.out.println("Car Color: " + color);
    }
}

public class Main {
    
    // Method that modifies the object's property
    static void changeColor(Car c) {
        c.color = "Blue";
    }

    public static void main(String[] args) {
        Car myCar = new Car();
        myCar.color = "Red";

        System.out.println("Before changing color:");
        myCar.displayColor();

        // Passing object to the method
        changeColor(myCar);

        System.out.println("After changing color:");
        myCar.displayColor();
    }
}


```
### Access Control Modifiers
- **public**: Accessible from everywhere.
- **private**: Accessible only within the class.
- **protected**: Accessible within the package and subclasses.
- **default(no modifier)**: Accessible within the package.

### Methods that Return values
Methods can return values using the `return` keyword
``` java
class Car {
    int getSpeed() {
        return 100;
    }

    public static void main(String[] args) {
        Car myCar = new Car();
        System.out.println("Speed: " + myCar.getSpeed());
    }
}
```
### Polymorphism
Polymorphism allows methods to be used in different ways.

### Method Overloading
 Method overloading is having multiple methods with the same name but different parameters.

``` java
class Car {
    void display(int speed) {
        System.out.println("Speed: " + speed);
    }

    void display(String color) {
        System.out.println("Color: " + color);
    }

    public static void main(String[] args) {
        Car myCar = new Car();
        myCar.display(120);
        myCar.display("Red");
    }
}
```
### Recursion
A method calling itself repeatedly until a base condition is met.
``` java
class Car {
    int factorial(int n) {
        if (n == 0) return 1;
        return n * factorial(n - 1);
    }

    public static void main(String[] args) {
        Car myCar = new Car();
        System.out.println("Factorial of 5: " + myCar.factorial(5));
    }
}
```

### Nested and Inner Classes
- **Nested Class:** A class defined inside another class
- **Inner Class:** A non-static nested class, associated with the outer class instance.
``` java
class Car {
    class Engine {
        void start() {
            System.out.println("Engine Started");
        }
    }

    public static void main(String[] args) {
        Car myCar = new Car();
        Car.Engine engine = myCar.new Engine();
        engine.start();
    }
}
```

