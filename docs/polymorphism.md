## What is an Polymorphism?

Polymorphism means "many forms", and it occurs when we have many classes that are related to each other by inheritance.

Like we specified in the previous chapter; [Inheritance](inheritance.md) lets us inherit attributes and methods from another class. **Polymorphism** uses those methods to perform different tasks. This allows us to perform a single action in different ways.

### Example

For example, think of a super-class called `Animal` that has a method called `animalSound()`. Sub-classes of Animals could be Pigs, Cats, Dogs, Birds - And they also have their own implementation of an animal sound (the pig oinks, and the cat meows, etc.):

```java
class Animal {
  public void animalSound() {
    System.out.println("The animal makes a sound");
  }
}



class Pig extends Animal {
  public void animalSound() {
    System.out.println("The pig says: wee wee");
  }
}

class Dog extends Animal {
  public void animalSound() {
    System.out.println("The dog says: bow wow");
  }
}

class Main {
  public static void main(String[] args) {
    Animal myAnimal = new Animal();  // Create a Animal object
    Animal myPig = new Pig();  // Create a Pig object
    Animal myDog = new Dog();  // Create a Dog object
    myAnimal.animalSound();
    myPig.animalSound();
    myDog.animalSound();
  }
}
```


---
## Compile-time Polymorphism (Static Polymorphism)

- Occurs when the **method to be executed is determined at compile time**.
- Achieved using:
    - **Method overloading** (same method name, different parameters) by use different method signature
	    - **method signature** = `method name` + `argument list ( number , and order of data type ) `
    - **Operator overloading** (in languages like C++)

### Example (Method Overloading in Java):

```java
class Calculator {
    int add(int a, int b) { return a + b; }
    double add(double a, double b) { return a + b; }  // Overloaded method
}

Calculator calc = new Calculator();
System.out.println(calc.add(5, 10));    // Calls int version
System.out.println(calc.add(5.5, 2.3)); // Calls double version

```

### Advantages:
- Faster execution because decisions are made at compile time
- Improves code readability and organization

> **Tip:** **Compile-time Polymorphism:** Decisions made **before execution** → fast, but fixed.
---
## Run-time Polymorphism (Dynamic Polymorphism)

- Occurs when the **method to be executed is determined at run time** based on the object type.
- Achieved using:
    - **Method overriding** (subclass provides its own implementation of a superclass method)
    - **Interfaces or Abstract classes**

### Example (Method Overriding in Java):

```java
class Animal {
    void sound() { System.out.println("Some sound"); }
}

class Dog extends Animal {
    void sound() { System.out.println("Bark"); }  // Overrides sound()
}

Animal myAnimal = new Dog();
myAnimal.sound();  // Output: Bark (determined at run-time)
```

### Advantages:
- Supports flexibility and dynamic behavior
- Allows a single interface to work with different object types

>**Tip:** **Run-time Polymorphism:** Decisions made **during execution** → flexible, but slightly slower.
---
## `@Override` Annotation in Java
- **`@Override`** is an **annotation** used above a method to indicate that the method is **intended to override a method in the super class**.
- It is **optional**, but highly recommended because it helps the compiler **catch errors** if the method does not correctly override a parent method.

### Key Points About `@Override`

1. Ensures that the method **actually overrides** a method from the super-class.
2. Helps catch **typos** in method names or incorrect parameter lists.
3. Can be used with **methods overriding super-class methods** or **implementing interface methods**.
4. Makes the code **more readable** and maintainable.

### Example

```java
class Animal {
    void sound() { System.out.println("Some sound"); }
}

class Dog extends Animal {
    @Override
    void sound() {  // Correctly overrides Animal's method
        System.out.println("Bark");
    }
}

class Cat extends Animal {
    // @Override
    void sounnd() {  // Compiler error if @Override is used: typo detected
        System.out.println("Meow");
    }
}
```

| Feature              | With `@Override`               | Without `@Override`              |
| -------------------- | ------------------------------ | -------------------------------- |
| Compiler check       | Ensures method truly overrides | No check; errors may be silent   |
| Readability          | Clear to programmer            | Less clear that method overrides |
| Typos in method name | Caught at compile time         | May lead to unexpected behavior  |





