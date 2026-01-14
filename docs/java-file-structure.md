# What is an Java Packages?

A package in Java is used to group related classes. Think of it as **a folder in a file directory**. We use packages to avoid name conflicts, and to write a better maintainable code. Packages are divided into two categories:
- Built-in Packages (packages from the Java API)
- User-defined Packages (create your own packages)


## Built-in Packages

The Java API is a library of prewritten classes, that are free to use, included in the Java Development Environment.

The library contains components for managing input, database programming, and much much more. The complete list can be found at [Oracles website](https://docs.oracle.com/javase/8/docs/api/).

The library is divided into **packages** and **classes**. Meaning you can either import a single class (along with its methods and attributes), or a whole package that contain all the classes that belong to the specified package.

To use a class or a package from the library, you need to use the `import` keyword:

```java
import package.name.Class;   // Import a single class
import package.name.*;   // Import the whole package
```

## Import a Class

If you find a class you want to use, for example, the `Scanner` class, **which is used to get user input**, write the following code:

### Example

```java
import java.util.Scanner;
```

In the example above, `java.util` is a package, while `Scanner` is a class of the `java.util` package.

To use the `Scanner` class, create an object of the class and use any of the available methods found in the `Scanner` class documentation. In our example, we will use the `nextLine()` method, which is used to read a complete line:

### Example

Using the `Scanner` class to get user input:

```java
import java.util.Scanner;

class Main {
  public static void main(String[] args) {
    Scanner myObj = new Scanner(System.in);
    System.out.println("Enter username");

    String userName = myObj.nextLine();
    System.out.println("Username is: " + userName);
  }
}
```

---

---

## Import a Package

There are many packages to choose from. In the previous example, we used the `Scanner` class from the `java.util` package. This package also contains date and time facilities, random-number generator and other utility classes.

To import a whole package, end the sentence with an asterisk sign (`*`). The following example will import ALL the classes in the `java.util` package:

### Example

```java
import java.util.*;
```

---

## User-defined Packages

To create your own package, you need to understand that Java uses a file system directory to store them. Just like folders on your computer:

### Example

```
└── root
  └── mypack
   └── MyPackageClass.java
```

To create a package, use the `package` keyword:

```java
package mypack;
class MyPackageClass {
  public static void main(String[] args) {
    System.out.println("This is my package!");
  }
}
```


# Java Environment Variable

A **Java environment variable** is a system-level setting that tells your computer where to find Java tools (like the **JDK** or **JRE**) and how to run Java programs. These variables are necessary so that commands like `java` and `javac` work from the command line without specifying the full path every time.


- **`JAVA_HOME`** 
	- Points to the installation directory of the Java Development Kit (JDK).
	- Example (Windows): `C:\Program Files\Java\jdk-21`
	- Example (Linux/macOS): `/usr/lib/jvm/java-21-openjdk`
- **`PATH`** 
	- A system variable that lists directories where executable programs are located.
	- You add the Java `bin` directory to it so you can run `java` and `javac` from any command prompt or terminal.
	-  Example (Windows): `%JAVA_HOME%\bin`
	- Example (Linux/macOS): `%JAVA_HOME%\bin`
- **`CLASSPATH`** 
	- Tells Java where to look for user-defined classes and packages.
	- Usually, it defaults to the current directory (`.`), and many modern setups don’t need it explicitly.

> Without setting these variables, your system won’t know where to find Java programs or compile Java code, causing errors like `'javac' is not recognized as an internal or external command`.

# Common Java-related file extensions

| **Extension**              | **Purpose / Description**                                                                |
| -------------------------- | ---------------------------------------------------------------------------------------- |
| `.java`                    | Java source code file. Contains classes, interfaces, enums, etc.                         |
| `.class`                   | Compiled Java bytecode file, produced by `javac`. Executed by JVM.                       |
| `.jar`                     | Java Archive. Packages `.class` files and resources into one executable or library file. |
| `.war`                     | Web Application Archive. Used to deploy Java web apps on servers.                        |
| `.ear`                     | Enterprise Archive. Used for Java EE (Enterprise Edition) applications.                  |
| `.jmod`                    | Java module file (Java 9+). Contains compiled classes, resources, and module info.       |
| `.properties`              | Configuration file storing key-value pairs for Java programs.                            |
| `.xml`                     | Often used for configuration (e.g., Spring, Maven `pom.xml`) in Java projects.           |
| `.mf`                      | Manifest file inside a `.jar`, contains metadata about the archive.                      |
| `.javafx`                  | Used in JavaFX projects (less common).                                                   |
| `.jnilib` / `.dll` / `.so` | Native libraries loaded by Java via JNI (platform-specific).                             |

💡 **Quick tip:**

- `.java` → source
- `.class` → compiled
- `.jar/.war/.ear` → packaged applications


