	**Java II(ADVANCED JAVA)**

**I.Exception:**  
**Checked Exception (Compile-time):** Checked by the compiler at compile time. You must handle these (try-catch) or declare them (throws). They typically represent external conditions beyond your immediate control, such as IOException or SQLException.

**Unchecked Exception (Runtime):** Not checked at compile time; they occur at runtime. They do not require mandatory handling. They usually represent programming bugs or logic errors, such as NullPointerException or ArrayIndexOutOfBoundsException

| Feature | Checked Exception | Unchecked Exception |
| :---- | ----- | ----- |
| Checked At | Compile time | runtime |
| Handling | Using *try-catch* block | Programmatic error, so debuggin skills should be good, wrote erro free code. |
| Parent class | *Exception* | *RunTimeException (Subclass of Exception).* |
| Cause | *External factors(File not found, Db crash)* | *Programmatic error or bug ridden code* |
| Example | *IoException,SqlException* | *NullpointerException, IllegalArgumentException.* |

Got it — you want **clean, structured notes**:  
👉 *Concept → short theory → code → explanation of what’s happening*  
👉 Enough detail to **understand deeply**, but still **10-min revision friendly**

---

# 

# 

# **🚀 1\. What is an Exception?**

## **🔹 Theory**

An **exception** is an event that interrupts the normal flow of a program. It occurs at **runtime** when something unexpected happens (divide by zero, null access, file not found). 👉 Java handles exceptions using **objects (class-based mechanism)**. All exceptions inherit from the `Throwable` class. The hierarchy is: `Throwable` (root) \-\> `Error` (serious JVM-related issues, rarely handled) and `Exception` (can be caught and handled). `Exception` is further divided into **Checked Exceptions** (must be handled/declared) and **Unchecked Exceptions** (subclasses of `RuntimeException`, typically indicating programming errors).

👉 Java handles exceptions using **objects (class-based mechanism)**.

---

## **💻 Code**

    `int a = 10 / 0;`

## **🧠 What happens?**

* JVM detects **divide by zero**  
* Creates `ArithmeticException` object  
* Stops normal execution  
* If not handled → program crashes

---

# 

# 

# **🚀 2\. try-catch (Handling Exception)**

## **🔹 Theory**

Used to **handle runtime errors** and prevent program crash. The `try` block contains the *risky code* that might throw an exception. The corresponding `catch` block is executed *only* if an exception of the declared type (or its subclass) occurs in the `try` block. This mechanism prevents the program from abnormally terminating and allows for graceful recovery or logging.

* `try` → risky code  
* `catch` → handles exception

**🚀 3\. Multiple catch**

## **🔹 Theory**

Different exceptions can be handled differently. When multiple `catch` blocks are present, the JVM attempts to match the thrown exception with the `catch` blocks **sequentially**. You must order catch blocks from the **most specific** exception (subclass, e.g., `NullPointerException`) to the **most general** exception (superclass, e.g., `Exception`). If the general exception is placed first, the specific ones will be unreachable (a compile-time error).

**💻 Code**  
    `try {`  
        `String s = null;`  
        `System.out.println(s.length());`  
    `} catch (NullPointerException e) {`  
        `System.out.println("Null issue");`  
    `} catch (Exception e) {`  
        `System.out.println("General issue");`  
    `}`

**🚀 4\. finally (Cleanup)**

## **🔹 Theory**

The `finally` block is guaranteed to execute regardless of whether an exception was thrown or caught in the `try-catch` block, or even if a `return` statement is encountered. It is essential for **resource cleanup** (e.g., closing connections, streams) to prevent resource leaks. The *only* time `finally` may not run is if the JVM exits during the `try` or `catch` block (e.g., via `System.exit()`).

* Whether exception occurs or not  
* Used for cleanup (closing file, DB)

**💻 Finally  in Code**  
    `try {`  
        `int a = 10 / 2;`  
    `} catch (Exception e) {`  
        `System.out.println("Error");`  
    `} finally {`  
        `System.out.println("Cleanup done");`  
    `}`

## 

## 

## 

## 

## 

## 

## **🚀 5\. throw (Manually throwing exception)**

## **🔹 Theory**

The `throw` keyword is used **inside a method** to explicitly create and instantiate a single exception object (`throw new ExceptionType(...)`) and transfer control to the nearest surrounding `try-catch` block or, if none exists, propagate it up the call stack. It is used to signal a specific error condition based on custom logic.

**💻 Code**  
    `int age = 15;`  
    `if (age < 18) {`  
        `throw new IllegalArgumentException("Not eligible");`  
    `}`

**🚀 6\. throws (Declaring exception)**

## **🔹 Theory**

The `throws` keyword is used in a method’s signature to **declare** that the method *might* throw one or more **checked exceptions**. This forces the calling method to either handle that exception using `try-catch` or re-declare it using `throws` to propagate it further up the call stack. This mechanism enforces the Java compiler's "handle or declare" rule for checked exceptions.

**💻 Code**  
    `import java.io.*;`  
    `void readFile() throws IOException {`  
        `throw new IOException("File error");`  
    `}`

---

# 

# **🚀 7\. Exception Propagation**

## **🔹 Theory**

When an exception occurs in a method, and that method does not contain a suitable `catch` block, the exception object is automatically "propagated" or moved up to the calling method in the call stack. This process continues until a method is found that contains a matching `catch` block. The propagation stops immediately once a matching `catch` block is found and executed. If the exception reaches the `main()` method and is still not handled, the program terminates abnormally.

**💻Exception Propagation Code**  
    `class Test {`  
        `void method1() {`  
            `int a = 10 / 0;`  
        `}`  
        `void method2() {`  
            `method1();`  
        `}`  
        `public static void main(String[] args) {`  
            `new Test().method2();`  
        `}`  
    `}`

# 

# 

# 

# 

# **🚀 8\. Catching Propagated Exception**

## **🔹 Theory**

Exception propagation allows a lower-level method to delegate the responsibility of handling an exception to a higher-level method in the call stack. This is often preferred in layered architectures. The key is that the propagation chain terminates immediately once a matching `catch` block is found and executed, and program execution continues safely from there.

**💻 Code**  
    `void method1() {`  
        `int a = 10 / 0;`  
    `}`  
    `void method2() {`  
        `try {`  
            `method1();`  
        `} catch (Exception e) {`  
            `System.out.println("Handled in method2");`  
        `}`  
    `}`

**🚀 9\. Uncaught Exception**

## **🔹 Theory**

An uncaught exception is an exception that is not handled by any `catch` block across the entire thread’s call stack, all the way up to the `main()` method. When this happens, the Java Virtual Machine (JVM) executes the default exception handler, which typically prints the stack trace to the console (showing exactly where the error occurred) and then halts the execution of the program thread.

**💻 Code**  
    `public static void main(String[] args) {`  
        `int a = 10 / 0;`  
    `}`

# **🚀 10\. Custom Exception (Subclassing)**

## **🔹 Theory**

Custom exceptions allow developers to define their own specific error types that align with the business logic of their application. By extending `Exception`, you create a **checked exception** (forcing the caller to handle it). By extending `RuntimeException`, you create an **unchecked exception** (allowing the caller to ignore it). Custom exceptions should always include a constructor that calls `super(msg)` to pass a meaningful message up the hierarchy.

* `Exception` (checked)  
* `RuntimeException` (unchecked)

---

## **💻 Code**

    `class InvalidAgeException extends Exception {`  
        `InvalidAgeException(String msg) {`  
            `super(msg);`  
        `}`  
    `}`

---

## **💻 Usage**

    `void checkAge(int age) throws InvalidAgeException {`  
        `if (age < 18) {`  
            `throw new InvalidAgeException("Too young");`  
        `}`  
    `}`

## **🧠 What happens?**

* Custom rule enforced  
* Exception behaves like built-in ones

---

# 

# **🚀 11\. Complete Flow Example**

    `public class Main {`  
        `static void check(int n) {`  
            `if (n < 0) {`  
                `throw new IllegalArgumentException("Negative");`  
            `}`  
        `}`  
        `public static void main(String[] args) {`  
            `try {`  
                `check(-5);`  
            `} catch (Exception e) {`  
                `System.out.println(e.getMessage());`  
            `} finally {`  
                `System.out.println("Execution finished");`  
            `}`  
        `}`  
    `}`

## **🧠 Flow**

* check() throws exception  
* caught in main  
* finally always runs

---

# **⚠️ COMMON MISTAKES**

1. ❌ Using `throw` instead of `throws`  
2. ❌ Catching general Exception first  
3. ❌ Ignoring finally  
4. ❌ Not understanding propagation

**🚀 JAVA 21 KEY FEATURES**  
---

**🚀 12\. Sealed Classes**

## **🔹 Theory**

**Sealed Classes** (introduced in JDK 17\) restrict which classes or interfaces can directly extend or implement them. This is a powerful feature for modeling **domain-specific hierarchies** where the set of subtypes is known and fixed. The `sealed` keyword is used on the parent class/interface, and the `permits` keyword lists the allowed subclasses. Subclasses must be declared as either `final`, `sealed`, or `non-sealed`. This enables the compiler to verify exhaustive checks in `switch` expressions that handle all permitted subclasses.

## **💻 Code**

```java
// Parent interface is sealed
sealed interface Shape permits Circle, Rectangle {
    // interface methods
}

// Subclass must be declared final, sealed, or non-sealed
final class Circle implements Shape {
    double radius;
}

non-sealed class Rectangle implements Shape {
    double length, width;
}
```

## **🧠 What happens?**

The interface `Shape` **explicitly limits** its implementations to `Circle` and `Rectangle`. Any attempt to create a third implementing class (e.g., `Triangle`) without permission will result in a **compile-time error**. This provides a stronger control over type hierarchies than standard inheritance.

**🚀 13\. Pattern Matching for switch**

## **🔹 Theory**

**Pattern Matching for switch** (finalized in JDK 21\) extends the `switch` statement and expression to allow pattern matching on the type of the switch selector, not just equality. This significantly reduces boilerplate by eliminating manual type checks (`instanceof`) and explicit casting, improving code safety and readability. It also enforces **exhaustiveness** for sealed types, ensuring all possible subclasses are handled. The case label now uses `case Type variable -> ...` syntax.

## **💻 Code**

```java
Object obj = new Rectangle(5, 10);

String result = switch (obj) {
    case Circle c -> "It's a Circle with radius: " + c.radius;
    case Rectangle r -> "It's a Rectangle with area: " + (r.length * r.width);
    default -> "Unknown shape";
};
```

## **🧠 What happens?**

The `switch` statement directly inspects the type of `obj`. When `obj` is a `Rectangle`, it matches the `case Rectangle r` pattern, and the local variable `r` is **automatically cast** to `Rectangle`, allowing direct access to its fields without explicit casting.

---

**🚀 14\. Sequenced Collections**

## **🔹 Theory**

**Sequenced Collections** (introduced in JDK 21\) introduces new interfaces (`SequencedCollection`, `SequencedSet`, `SequencedMap`) to standardize operations on collections that have a **defined encounter order**. This unifies methods for accessing the first/last elements or reversing the order. The new interfaces provide consistent methods like `getFirst()`, `getLast()`, and a `reversed()` view across the API.

## **💻 Code**

```java
import java.util.SequencedCollection;
import java.util.LinkedList;

SequencedCollection<String> list = new LinkedList<>();
list.addLast("A");
list.addLast("B");
list.addLast("C");

// Consistent access methods
String first = list.getFirst();
SequencedCollection<String> reversed = list.reversed();
```

## **🧠 What happens?**

The `list` maintains its insertion order. The `SequencedCollection` interface guarantees access to the first element via `getFirst()`. The powerful `reversed()` method provides a **reverse-ordered view** of the collection without creating a new copy.

---

**🚀 15\. Virtual Threads**

## **🔹 Theory**

**Virtual Threads** (Project Loom, finalized in JDK 21\) are lightweight, low-overhead threads implemented by the JVM, not the operating system. They dramatically increase the number of concurrent tasks a server application can handle by allowing millions of virtual threads to map onto a small pool of high-cost **platform threads**. Virtual threads are primarily designed for executing blocking I/O operations cheaply, simplifying concurrent programming into a thread-per-request style.

## **💻 Code**

```java
import java.util.concurrent.Executors;

Runnable task = () -> {
    System.out.println("Running on a Virtual Thread.");
};

// Create and start a virtual thread
Thread.ofVirtual().start(task);

// Or use the executor service
try (var executor = Executors.newVirtualThreadPerTaskExecutor()) {
    executor.submit(task);
}
```

## **🧠 What happens?**

The `Thread.ofVirtual().start(task)` creates a new virtual thread. When it blocks on I/O, the JVM **unmounts** it from its underlying platform thread, freeing the platform thread to serve other virtual threads. This allows for massive concurrency with simple, sequential code.

