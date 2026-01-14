## What is Class ?

- A **class** is a blueprint or template for creating objects.
- It defines **attributes (data)** and **methods (functions)** that the objects will have.
- A class itself is not a real entity; it’s just a description of what objects should contain and do.
- A class itself **does not occupy memory** until an object is created.

---
## Advantages of classes:
- Organize code logically around real-world concepts
- Promote **code re-usability** by allowing multiple objects from the same class
- Make programs easier to maintain, modify, and debug

---
## Access Modifiers
- For **classes**, you can use either `public` or _default_:

| Modifier  | Description                                                                                                                                                                                                                 |
| --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `public`  | The class is accessible by any other class                                                                                                                                                                                  |
| _default_ | The class is only accessible by classes in the same package. This is used when you don't specify a modifier. You will learn more about packages in the [Packages chapter](https://www.w3schools.com/java/java_packages.asp) |
	
---
## Non-Access Modifiers
- For **classes**, you can use either `final` or `abstract`:

| Modifier   | Description                                                                                                                                                                                                                                                                                                                     | Try it |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------ |
| `final`    | The class cannot be inherited by other classes (You will learn more about inheritance in the [Inheritance chapter](https://www.w3schools.com/java/java_inheritance.asp))                                                                                                                                                        |        |
| `abstract` | The class cannot be used to create objects (To access an abstract class, it must be inherited from another class. You will learn more about inheritance and abstraction in the [Inheritance](https://www.w3schools.com/java/java_inheritance.asp) and [Abstraction](https://www.w3schools.com/java/java_abstract.asp) chapters) |        |

> **Tip:** Think of a class as a recipe or blueprint—it tells you how to create something, but it is not the actual thing itself.

---
## Java Inner Classes

In Java, it is also possible to nest classes (a class within a class). The purpose of nested classes is to group classes that belong together, which makes your code more readable and maintainable.

To access the inner class, create an object of the outer class, and then create an object of the inner class:

### Example

```java
class OuterClass {
  int x = 10;

  class InnerClass {
    int y = 5;
  }
}

public class Main {
  public static void main(String[] args) {
    OuterClass myOuter = new OuterClass();
    OuterClass.InnerClass myInner = myOuter.new InnerClass();
    System.out.println(myInner.y + myOuter.x);
  }
}

// Outputs 15 (5 + 10)
 
```

---

## Private Inner Class

Unlike a "regular" class, an inner class can be `private` or `protected`. If you don't want outside objects to access the inner class, declare the class as `private`:

### Example

```java
class OuterClass {
  int x = 10;

  private class InnerClass {
    int y = 5;
  }
}

public class Main {
  public static void main(String[] args) {
    OuterClass myOuter = new OuterClass();
    OuterClass.InnerClass myInner = myOuter.new InnerClass();
    System.out.println(myInner.y + myOuter.x);
  }
}
 
```

If you try to access a private inner class from an outside class, an error occurs:

`Main.java:13: error: OuterClass.InnerClass has private access in OuterClass       OuterClass.InnerClass myInner = myOuter.new InnerClass();                 ^`

---

---

## Static Inner Class

An inner class can also be `static`, which means that you can access it without creating an object of the outer class:

### Example

```java
class OuterClass {
  int x = 10;

  static class InnerClass {
    int y = 5;
  }
}

public class Main {
  public static void main(String[] args) {
    OuterClass.InnerClass myInner = new OuterClass.InnerClass();
    System.out.println(myInner.y);
  }
}

// Outputs 5
 
```

**Note:** just like `static` attributes and methods, a `static` inner class does not have access to members of the outer class.

---

## Access Outer Class From Inner Class

One advantage of inner classes, is that they can access attributes and methods of the outer class:

### Example

```java
class OuterClass {
  int x = 10;

  class InnerClass {
    public int myInnerMethod() {
      return x;
    }
  }
}

public class Main {
  public static void main(String[] args) {
    OuterClass myOuter = new OuterClass();
    OuterClass.InnerClass myInner = myOuter.new InnerClass();
    System.out.println(myInner.myInnerMethod());
  }
}

// Outputs 10
```

## Built-in Methods in a Class (Inherited from `Object`)

The **full path** (fully qualified name) of the `Object` class in Java is:

`java.lang.Object`

- **`java`** → top-level package
    
- **`lang`** → subpackage containing fundamental classes
    
- **`Object`** → the class itself

| Method               | Default Implementation / Behavior                                                                 | Description                                |
| -------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------ |
| `toString()`         | Returns `getClass().getName() + '@' + Integer.toHexString(hashCode())`                            | String representation of the object.       |
| `equals(Object obj)` | Compares **references**: `this == obj`                                                            | Checks if two objects are the same object. |
| `hashCode()`         | Returns **unique integer based on memory address**                                                | Hash code of the object.                   |
| `getClass()`         | Returns the **runtime class** of the object                                                       | Useful to get object type at runtime.      |
| `clone()`            | Creates a **shallow copy** of the object (throws `CloneNotSupportedException` if not `Cloneable`) | Copies the object.                         |
| `finalize()`         | Called by **garbage collector** before object is destroyed                                        | Allows cleanup before destruction.         |
| `notify()`           | Wakes up **one thread** waiting on this object                                                    | Thread communication.                      |
| `notifyAll()`        | Wakes up **all threads** waiting on this object                                                   | Thread communication.                      |
| `wait()`             | Causes current thread to **wait** until notified                                                  | Thread synchronization.                    |