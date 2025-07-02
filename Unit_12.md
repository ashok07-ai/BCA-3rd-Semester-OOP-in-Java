# Introduction to Java Applets
### Definition of Applet
An Applet is a small Java program that runs inside a web browser or an applet viewer.

- It is used for creating interactive features in web pages such as animations, games, or GUI-based utilities. 
- Unlike standalone applications, applets do not have a `main()` method.
- Applets are subclasses of `java.applet.Applet` or `javax.swing.JApplet`.

#### Applet Lifecycle Methods
The lifecycle of an applet is managed by the browser or applet viewer, and consists of the following methods:
| Method  | Description  | 
|------------|-------|
| `init()`   | Called once when the applet is first loaded. Used for initialization.  | 
| `start()`  | Called each time the applet becomes visible (starts or resumes execution). | 
| `stop()`    | Called when the applet becomes hidden (pause/stop execution). |
| `destroy()`    | Called when the applet is removed from memory. Cleanup code goes here. |
| `paint(Graphics g)`    | Called to draw graphics or output on the applet window. |

### Building a Simple Applet
```java
import java.applet.Applet;
import java.awt.Graphics;

/*
<applet code="SimpleApplet" width="300" height="200"></applet>
*/

public class SimpleApplet extends Applet {
    public void paint(Graphics g) {
        g.drawString("Hello, I am an Applet!", 50, 100);
    }
}
```
### Using Applet Viewer
**Steps**:
1. Compile the applet:
``` java
javac SimpleApplet.java
```
2. Run the applet using applet viewer
``` java
appletviewer SimpleApplet.java
```
**Note**: You must write the `<applet>` tag as a comment in the source file for appletviewer to recognize it.

### Adding Controls to Applet
Applets can contain GUI controls like buttons, labels, text fields, etc., using AWT components.

``` java
import java.applet.Applet;
import java.awt.*;

public class ControlApplet extends Applet {
    public void init() {
        Label label = new Label("Enter Name:");
        TextField tf = new TextField(15);
        Button btn = new Button("Submit");
        
        add(label);
        add(tf);
        add(btn);
    }
}
```
### Animation Concepts in Applet
Applets can perform simple animations using:
- Repeated calls to repaint() method.
- Using Thread to control timing.

```java
import java.applet.Applet;
import java.awt.*;
import java.util.*;

public class AnimationApplet extends Applet implements Runnable {
    int x = 0;
    Thread t;

    public void init() {
        t = new Thread(this);
        t.start();
    }

    public void run() {
        while (true) {
            x += 10;
            if (x > getWidth()) x = 0;
            repaint();
            try { Thread.sleep(100); } catch (InterruptedException e) {}
        }
    }

    public void paint(Graphics g) {
        g.drawString("Moving Text", x, 100);
    }
}
```

