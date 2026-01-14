## What is a Dynamic Binding in Java

- **Dynamic Binding** (also called **late binding**) happens when the **method to be executed is determined at run-time**, depending on the **actual object type**, not the reference type.
- It is a key concept behind **run-time polymorphism**.

---

## Non-Static Method Overriding (Dynamic Binding)

```java
class Animal {
    void sound() { System.out.println("Animal sound"); }
}
class Dog extends Animal {
    void sound() { System.out.println("Dog barks"); }
}
public class Test {
    public static void main(String[] args) {
        Animal a = new Dog();
        a.sound();  // Calls Dog's version at run-time
		      // Output : Dog barks
    }
}
```

- **Key Points:**    
    - Instance methods are **dynamically bound**.
    - JVM determines at **run-time** which method to execute based on **actual object type**.
---
## Static Method Hiding (No Dynamic Binding)

```java
class Animal {
    static void sound() { System.out.println("Animal sound"); }
}

class Dog extends Animal {
    static void sound() { System.out.println("Dog barks"); }
}

public class Test {
    public static void main(String[] args) {
        Animal a = new Dog();
        a.sound();  // Calls Animal.sound() at compile-time
                    // Output: Animal sound
    }
}
```

- **Key Points:**
    - Static methods are **not dynamically bound**.
    - Method call is resolved at **compile-time** based on **reference type**.

---
## Dynamic Binding vs Static Binding

| Feature           | Non-Static Method  | Static Method         |
| ----------------- | ------------------ | --------------------- |
| Binding Type      | Dynamic (Run-time) | Static (Compile-time) |
| Method Resolution | Actual object type | Reference type        |
| Polymorphism      | Yes (Overriding)   | No (Hiding)           |
| `@Override`       | Allowed            | Not allowed           |
| Example Output    | `Dog barks`        | `Base static`         |

> **Tip:** Dynamic binding allows Java to support **flexible run-time behavior**, while static methods always follow the **reference type** at compile-time.

---

Here’s a detailed explanation in your style of the difference between

```java
Animal a = new Dog();
```

and

```java
Dog a = new Dog();
```

and how it behaves with **overriding (dynamic binding)** and **static methods (static binding)**.

---

## Reference Type vs Object Type

- **Reference type** → The type used in the declaration (`Animal` or `Dog`)
- **Object type** → The actual class of the object created (`new Dog()`)

| Reference | Object | Non-static Method (Overriding / Dynamic Binding) | Static Method (Static Binding)                       |
| --------- | ------ | ------------------------------------------------ | ---------------------------------------------------- |
| Animal    | Dog    | Dog’s method                                     | <p style = " color : red;"> **Animal’s method** </p> |
| Dog       | Dog    | Dog’s method                                     | Dog’s method                                         |

---

## Case: `Animal a = new Dog();`

- **Reference type:** `Animal`
- **Object type:** `Dog`

### ✅ Non-static (Overriding / Dynamic Binding)

```java
class Animal { void sound() { System.out.println("Animal sound"); } }
class Dog extends Animal { void sound() { System.out.println("Dog barks"); } }

Animal a = new Dog();
a.sound();  // Output: Dog barks
```

- **Behavior:**
    - JVM looks at **object type (`Dog`) at run-time**
    - Calls **overridden method in Dog** → dynamic binding
### ❌ Static (Static Binding)

```java
class Animal { static void sound() { System.out.println("Animal sound"); } }
class Dog extends Animal { static void sound() { System.out.println("Dog barks"); } }

Animal a = new Dog();
a.sound();  // Output: Animal sound
```

- **Behavior:**
    - Compiler looks at **reference type (`Animal`)**
    - Calls **static method in Animal** → static binding

---
## Case: `Dog a = new Dog();`

- **Reference type:** `Dog`
- **Object type:** `Dog`

### ✅ Non-static (Overriding / Dynamic Binding)

```java
class Animal { void sound() { System.out.println("Animal sound"); } }
class Dog extends Animal { void sound() { System.out.println("Dog barks"); } }

Dog a = new Dog();
a.sound();  // Output: Dog barks
```

- **Behavior:**
    - JVM sees object type = reference type = `Dog`
    - Calls **Dog’s method** → dynamic binding works as expected
### ❌ Static (Static Binding)

```java
class Animal { void sound() { System.out.println("Animal sound"); } }
class Dog extends Animal { void sound() { System.out.println("Dog barks"); } }

Dog a = new Dog();
a.sound();  // Output: Dog barks
```

- **Behavior:**
    - Reference type is `Dog` → compiler calls **Dog’s static method**
    - Static binding uses **reference type**, works as expected
---

> **Tip:**

- **Dynamic binding**: depends on **object type at run-time** → only non-static methods
    
- **Static binding**: depends on **reference type at compile-time** → static methods
    

---
