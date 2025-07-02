# AWT & Swing in Java
### About AWT (Abstract Window Toolkit)
- Part of the `java.awt` package.
- Used to create GUI components (windows, buttons, etc.).
- Heavyweight components — depend on the native OS.

### About Swing
- Part of `javax.swing` package.
- Provides rich, flexible GUI components.
- Lightweight components — do not depend on OS.
- Built on top of AWT but more powerful and portable.

### About `JFrame` (Top-Level Window in Swing)
`JFrame` is the main window for Swing applications.

```java
import javax.swing.*;

public class MyFrame {
    public static void main(String[] args) {
        JFrame frame = new JFrame("My Swing Window");
        frame.setSize(300, 200);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setVisible(true);
    }
}
```
### Swing Components
JLabel — Displays text/images.
- **JTextField** — Single-line text input.
- **JButton** — Clickable button.
- **JTextArea** — Multi-line text input.
- **JCheckBox** — Choice with check/uncheck option.
- **JRadioButton** — Mutually exclusive options (used with ButtonGroup).
- **JComboBox** — Drop-down selection box.
- **JList** — Displays a list of selectable items.
- **JTable** — Displays data in tabular form.
- **JPanel** — A container for organizing components.
- **JDesktopPane** — For MDI (Multiple Document Interface).
- **JInternalFrame** — Child window inside desktop pane.

### Event Handling in Swing Applications
Swing uses Event Listeners to handle user actions. <br>
**Example**: ActionListener for a button:
```java
JButton button = new JButton("Click");
button.addActionListener(e -> System.out.println("Button Clicked"));
```
### Layout Management
Controls component placement inside containers.
- `FlowLayout` — Arranges components left to right.
- `BorderLayout` — Divides container into North, South, East, West, Center.
- `GridLayout` — Arranges components in a grid (rows & columns).

### Using `JPanel`
A container for grouping components. Can be nested.

###  Choice Components
`JCheckBox`, `JRadioButton`, `JComboBox`, `JList`

```java
JCheckBox cb = new JCheckBox("Accept Terms");
JRadioButton rb1 = new JRadioButton("Male");
JComboBox<String> combo = new JComboBox<>(new String[]{"Java", "Python"});
```
### Borders in Swing
Swing provides border options to enhance UI.
```java
JPanel panel = new JPanel();
panel.setBorder(BorderFactory.createTitledBorder("User Info"));
```
### `JList` and its Events with MVC Pattern
`JList` follows MVC (Model-View-Controller) where:

- Model: Holds the data
- View: Displays the list
- Controller: Handles user interaction

```java
JList<String> list = new JList<>(new String[]{"A", "B", "C"});
list.addListSelectionListener(e -> System.out.println("Selected: " + list.getSelectedValue()));
```
### Key & Mouse Event Handling
**KeyListener Example:**
```java
textfield.addKeyListener(new KeyAdapter() {
    public void keyPressed(KeyEvent e) {
        System.out.println("Key Pressed: " + e.getKeyChar());
    }
});
```
**MouseListener Example:**
```java
button.addMouseListener(new MouseAdapter() {
    public void mouseClicked(MouseEvent e) {
        System.out.println("Mouse Clicked");
    }
});
```
### Menus in Swing
Menus provide navigation and options.
```java 
JMenuBar menuBar = new JMenuBar();
JMenu fileMenu = new JMenu("File");
JMenuItem exitItem = new JMenuItem("Exit");
fileMenu.add(exitItem);
menuBar.add(fileMenu);
frame.setJMenuBar(menuBar);
```
### Dialog Boxes in Swing
Used to show messages or take input.
``` java
JOptionPane.showMessageDialog(frame, "Operation Successful");
```

`JTable` for Displaying Data in Tabular Form
```java
String[] columns = {"ID", "Name"};
String[][] data = {{"1", "John"}, {"2", "Alice"}};
JTable table = new JTable(data, columns);
frame.add(new JScrollPane(table));
```
### MDI using `JDesktopPane` & `JInternalFrame`
```java
JDesktopPane desktop = new JDesktopPane();
JInternalFrame internal = new JInternalFrame("Child", true, true, true, true);
internal.setSize(200, 150);
internal.setVisible(true);
desktop.add(internal);
frame.add(desktop);
```
### Using IDE like NetBeans, JBuilder for Drag & Drop
- NetBeans, JBuilder provide GUI builders for creating Swing applications using drag & drop.
- Generates background code automatically.
- Speeds up development.

### Adapter Classes
Adapter classes provide empty implementations for listener interfaces. Useful when only specific methods need to be overridden.

Example with `MouseAdapter`:
```java
button.addMouseListener(new MouseAdapter() {
    public void mouseClicked(MouseEvent e) {
        System.out.println("Clicked");
    }
});
```
