# Welcome to Java Programming Notes

## Overview

Object-Oriented Programming (OOP) is a programming paradigm that organizes code around **objects** that contain both **data (attributes)** and **functions (methods)**. It provides a clear structure, promotes code reusability, and makes programs easier to maintain.

---

## Core OOP Concepts

### 1. [Classes and Objects](class.md)

- **Class:** A blueprint or template for creating objects
- **Object:** An instance of a class with its own data and state
- Classes define **attributes** and **methods** that objects will have
- Access Modifiers: `public`, `private`, `protected`, _default_
- Non-Access Modifiers: `final`, `abstract`, `static`

### 2. [Encapsulation](encapsulation.md)

- Hide sensitive data from users using `private` access modifier
- Provide public **getter** and **setter** methods to control access
- Protects data integrity and allows validation of values
- Key principle: "Make data private, provide public accessors"

### 3. [Inheritance](inheritance.md)

- **Subclass** inherits attributes and methods from **superclass**
- Use `extends` keyword to inherit from a class
- Use `super` to reference parent class methods/constructors
- Use `final` keyword to prevent a class from being inherited
- Promotes code reusability and establishes hierarchical relationships

### 4. [Polymorphism](polymorphism.md)

- Means "many forms" — perform a single action in different ways
- Two types:
  - **Compile-time (Static):** Method overloading
  - **Run-time (Dynamic):** Method overriding
- Related concept: [Dynamic Binding ( Late binding )](dynamic-binding.md) — method determined at run-time based on object type

### 5. [Abstraction](abstraction.md)

- Hide complex details and show only essential information
- Achieved through:
  - **Abstract Classes:** Use `abstract` keyword, cannot instantiate directly
  - **Interfaces:** Completely abstract classes, define contracts
- Abstract methods have no body; implementation provided by subclasses/implementing classes
- Abstraction is the concept of defining real world objects in terms of classes or interfaces.

---

## OOP Design Principles

| Principle | Description | Key Points |
| --- | --- | --- |
| **Encapsulation** | Hide internal state, provide controlled access | Private data + public methods |
| **Inheritance** | Reuse code through hierarchical relationships | Extends classes, use `super` |
| **Polymorphism** | Use the same interface for different types | Overriding & method overloading |
| **Abstraction** | Show only what's necessary, hide complexity | Abstract classes & interfaces |

---

## How OOP Concepts Work Together

```
┌─────────────────────────────────────────────────┐
│                  ABSTRACTION                    │
│  (Define what objects should do - abstract)     │
└─────────────────────────┬───────────────────────┘
                          │
                          ↓
┌─────────────────────────────────────────────────┐
│            CLASS (Blueprint)                    │
│  - Attributes (Data) with ENCAPSULATION         │
│  - Methods (Behavior)                           │
└─────────────────────────┬───────────────────────┘
                    │
         ┌────────────────┴─────────────────┐
         │                                  │
         ↓                                  ↓
   [INHERITANCE]                         [OBJECT]
 (Subclass extends                 (Instance of the class)
    superclass)                             |
         │                                  |
         └────────────────┬─────────────────┘
                          ↓
        ┌──────────────────────────┐
        │   POLYMORPHISM           │
        │ (Different behaviors for │
        │  related classes)        │
        └──────────────────────────┘
```

---

## Key OOP Keywords

| Keyword | Purpose | Related Concept |
| --- | --- | --- |
| `class` | Define a class blueprint | [Classes and Objects](class.md) |
| `extends` | Inherit from a superclass | [Inheritance](inheritance.md) |
| `super` | Reference parent class | [Inheritance](inheritance.md) |
| `implements` | Implement an interface | [Abstraction](abstraction.md) |
| `abstract` | Define abstract class/method | [Abstraction](abstraction.md) |
| `interface` | Define a contract | [Abstraction](abstraction.md) |
| `private` | Hide data | [Encapsulation](encapsulation.md) |
| `public` | Make accessible | [Encapsulation](encapsulation.md) |
| `protected` | Accessible in subclasses | [Inheritance](inheritance.md) |
| `final` | Prevent overriding/inheritance | [Inheritance](inheritance.md), [Polymorphism](polymorphism.md) |
| `@Override` | Mark overriding methods | [Polymorphism](polymorphism.md) |

---

## Common Patterns

### Example: Full OOP Implementation

```java
// ABSTRACTION: Define what animals should do
abstract class Animal {
    abstract void sound();  // Abstract method
    public void sleep() {   // Concrete method
        System.out.println("Zzz");
    }
}

// INHERITANCE: Dog inherits from Animal
class Dog extends Animal {
    private String name;  // ENCAPSULATION: private attribute

    // ENCAPSULATION: provide getter
    public String getName() {
        return name;
    }

    // POLYMORPHISM: override abstract method
    @Override
    void sound() {
        System.out.println("Bark");
    }
}

// POLYMORPHISM: Same reference type, different object types
Animal myDog = new Dog();
myDog.sound();  // Calls Dog's version (Dynamic Binding)
```

---

## Related Resources

- [Basic Java Notes](basic-notes.md) — Primitive & non-primitive types, type casting
- [Java File Structure](java-file-structure.md) — Organize classes into packages
- [Dynamic Binding ( Late binding )](dynamic-binding.md) — How Java resolves method calls at run-time

---

## Key Advantages of OOP

✅ Clear structure for programs  
✅ Code reusability through inheritance & composition  
✅ Easier to maintain, modify, and debug  
✅ Follows DRY principle ("Don't Repeat Yourself")  
✅ Supports flexible and dynamic behavior through polymorphism  
✅ Better security through encapsulation

---

## Quick Navigation

Use the navigation menu above to explore different topics. Each section builds upon previous concepts, so we recommend following the order if you're new to Java.

---

*Happy Learning! 📚*


