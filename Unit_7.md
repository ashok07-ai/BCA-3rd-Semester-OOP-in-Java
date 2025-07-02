# Multithreading in Java
Multithreading is a Java feature that allows the execution of multiple threads simultaneously, improving performance by utilizing CPU efficiently.

### Creating/Instantiating/Starting New Threads
**Extending `java.lang.Thread` Class**

One way to create a `thread` is by extending the Thread class and overriding the `run()` method.

``` java
class MyThread extends Thread {
    public void run() {
        System.out.println("Thread is running...");
    }
}

public class Example {
    public static void main(String[] args) {
        MyThread t1 = new MyThread();
        t1.start();  // Starts the thread
    }
}

```

**Implementing java.lang.Runnable Interface**

Another way is by implementing the `Runnable` interface and passing it to a `Thread` object.
```java
class MyRunnable implements Runnable {
    public void run() {
        System.out.println("Thread is running...");
    }
}

public class Example {
    public static void main(String[] args) {
        MyRunnable r = new MyRunnable();
        Thread t1 = new Thread(r);
        t1.start();  // Starts the thread
    }
}
```
### Understand Thread Execution
The `start()` method starts a new thread and invokes the `run()` method internally.

Calling `run()` directly will not start a new thread; it will behave like a normal method.

### Thread Priorities
Java threads have priorities ranging from **1 (MIN_PRIORITY)** to **10 (MAX_PRIORITY)**. Default priority is **5 (NORM_PRIORITY)**.

```java
Thread t1 = new Thread();
t1.setPriority(Thread.MAX_PRIORITY);
```
Thread priorities are just hints; actual scheduling depends on the JVM and OS.

### Synchronization
When multiple threads access shared resources, data inconsistency can occur. Synchronization prevents this by allowing only one thread at a time to access the critical section.

**Using `synchronized` Keyword:**
``` java
class Counter {
    int count = 0;

    synchronized void increment() {
        count++;
    }
}
```
### Inter-Thread Communication
Threads can communicate using the following methods of `Object` class:

`wait()` → Causes the current thread to wait.

`notify()` → Wakes up a single waiting thread.

`notifyAll()` → Wakes up all waiting threads.

``` java
class Shared {
    synchronized void printMessage() {
        try {
            wait();  // Wait until notified
            System.out.println("Message printed");
        } catch (InterruptedException e) {
            System.out.println(e);
        }
    }

    synchronized void trigger() {
        notify();  // Notify waiting thread
    }
}
```
### Deadlock
Deadlock occurs when two or more threads are waiting for each other to release locks, and none of them can proceed.

``` java
class A {
    synchronized void methodA(B b) {
        System.out.println("Thread A starts execution of methodA");
        try { Thread.sleep(100); } catch (Exception e) {}
        b.last();
    }

    synchronized void last() {
        System.out.println("Inside A's last method");
    }
}

class B {
    synchronized void methodB(A a) {
        System.out.println("Thread B starts execution of methodB");
        try { Thread.sleep(100); } catch (Exception e) {}
        a.last();
    }

    synchronized void last() {
        System.out.println("Inside B's last method");
    }
}

public class DeadlockExample {
    public static void main(String[] args) {
        A a = new A();
        B b = new B();

        Thread t1 = new Thread(() -> a.methodA(b));
        Thread t2 = new Thread(() -> b.methodB(a));

        t1.start();
        t2.start();
    }
}
```
### How to Avoid Deadlock:
- Acquire locks in a fixed, consistent order.

- Minimize synchronized blocks.

- Use timeout mechanisms if possible.



