## What is OOP?

* ### Procedural programming
	is about writing procedures or methods that perform operations on the data, while object-oriented programming is about creating objects that contain both data and methods.

* ### Object-Oriented Programming (OOP) 
	is a programming approach where programs are organized around **objects**, which combine **data (attributes)** and **functions (methods)** to model real-world entities and behaviors.

* ### Object-oriented programming has several advantages over procedural programming:
	* OOP is faster and easier to execute
	- OOP provides a clear structure for the programs
	- OOP helps to keep the code DRY **"Don't Repeat Yourself"**, and makes the code easier to maintain, modify and debug
	- OOP makes it possible to create full reusable applications with less code and shorter development time

>**Tip:** The "Don't Repeat Yourself" (DRY) principle is about reducing the repetition of code. You should extract out the codes that are common for the application, and place them at a single place and reuse them instead of repeating it.

---
## What is an Object?

- An **object** is an instance of a class.
- It represents a real-world entity with **its own data** and the ability to **perform actions** defined by the class.
- Objects are created using the class and can interact with other objects in the program.

- ### Advantages of objects:
    - Bring the class blueprint to life with actual data
    - Allow multiple independent instances with different values
    - Support OOP principles like 
	    - [[Software Engineering/Java Notes/encapsulation.md|Encapsulation]]
	    - [[Software Engineering/Java Notes/inheritance.md|Inheritance]]
	    - [[Software Engineering/Java Notes/Polymorphism|Polymorphism]]
	    - [[Software Engineering/Java Notes/abstraction.md|Abstraction]] ( Data Abstraction )
	    - [[Dynamic Binding ( Late binding )|Dynamic Binding ( Late binding )]]

> **Tip:** Think of a class as a blueprint and an object as the actual thing built from it, like a house built from a plan.

---
## What is an Attribute?

- An **attribute** is a variable or property that belongs to a class or object.
- It stores **data** about the object, representing its characteristics or state.
- Attributes define **what an object has**, such as a name, age, color, or size.
	
- ### Advantages of attributes:
    - Keep the data of an object organized
    - Help represent real-world characteristics in programs
    - Make objects unique by allowing each object to have different attribute values
	
- ### Access Modifiers
	* For **attributes, methods and constructors**, you can use the one of the following:
	
| Modifier    | Description                                                                                                                                                                                                     |
| ----------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `public`    | The code is accessible for all classes                                                                                                                                                                          |
| `private`   | The code is only accessible within the declared class                                                                                                                                                           |
| _default_   | The code is only accessible in the same package. This is used when you don't specify a modifier. You will learn more about packages in the [Packages chapter](https://www.w3schools.com/java/java_packages.asp) |
| `protected` | The code is accessible in the same package and **subclasses**. You will learn more about subclasses and superclasses in the [Inheritance chapter](https://www.w3schools.com/java/java_inheritance.asp)          |
	
* ## Non-Access Modifiers
	* For **attributes and methods**, you can use the one of the following:

|Modifier|Description|
|---|---|
|`final`|Attributes and methods cannot be overridden/modified|
|`static`|Attributes and methods belong to the class, not to objects. This means all objects share the same `static` attribute, and `static` methods can be called without creating objects.|
|`abstract`|Can only be used in an abstract class, and can only be used on methods. The method does not have a body, for example `abstract void run();`. The body is provided by the subclass (inherited from). You will learn more about inheritance and abstraction in the [Inheritance](https://www.w3schools.com/java/java_inheritance.asp) and [Abstraction](https://www.w3schools.com/java/java_abstract.asp) chapters|
|`transient`|Attributes and methods are skipped when serializing the object containing them|
|`synchronized`|Methods can only be accessed by one thread at a time|
|`volatile`|The value of an attribute is not cached thread-locally, and is always read from the "main memory"|


> **Tip:** Think of attributes as the features of an object—like the color, model, and speed of a car object.

---
## What is a Constructor?

- A **constructor** is a special method in a class that is automatically called when an **object** is created.
- It is used to **initialize the object’s attributes** with default or provided values.
- Constructors usually have the **same name as the class** and do not have a return type.


- ### Types of Constructors with Examples:
	1. **Default Constructor** – A constructor with **no parameters**.

		```java
		class Car 
		{
		    String color;
		    public Car() {  // Default constructor
			 color = "Red";
		    }
		};
		
		Car myCar;  // color is automatically set to "Red"
		```
		
	2. **Parameterized Constructor** – A constructor that **accepts arguments** to initialize the object.

		```java
		class Car 
		{
		    String color;
		    public Car(string c) {  // Parameterized constructor
			 color = c;
		    }
		};
			
		Car myCar("Blue");  // color is set to "Blue"
		```
		
	3. **Copy Constructor** – A constructor that **creates a new object as a copy** of an existing object.
		
		```java
		class Car 
		{
		    String color;
		    public Car(Car other) { // Copy constructor
		        this.color = other.color;
		    }
		};
			
		Car myCar("Blue");  // color is set to "Blue"
		```
		
	4. **Static Constructor (Not in Java)** – Used in languages like C# to initialize static members of a class before any object is created.
	5. **Private Constructor (Not directly in Java, but achievable via patterns)** – Prevents external code from creating objects; often used in **Singleton pattern**.
	6. **Conversion Constructor (Not in Java)** – A constructor that converts one type into another.
	
- ### **Using `super` in Constructors**
	- The `super` keyword is used in a child class constructor to **call a constructor of the parent class**.
	- It **must be the first statement** in the child class constructor.
	- This ensures that the **parent class is properly initialized** before initializing the child class.
	- You can also add **messages** in constructors to see the order in which parent and child constructors are called.
	
	```java
		class Car extends Vehicle 
		{
		    private String color;
			
		    public Car(String brand, String color) 
		    {
		        super(brand); // Call parent constructor
		        this.color = color;
		        System.out.println("Car constructor called. Color set to: " + color);
		    }
	    }
	```
	
- ### Advantages of constructors:    
    - Automatically set up an object when it is created
    - Ensure that objects start in a valid state
    - Reduce the need to call separate methods to initialize objects
	
- ### Access Modifiers 
	- check at attributes

> **Tip:** Think of a constructor as a setup routine for an object—like filling a new car with fuel and setting the seats before driving.

---
## What is a Constructor Java OOP Keywords?

- ### this
	- Refers to the **current object**.
	- Often used to distinguish between **instance variables** and parameters.
	- **Example:** `this.color = color;`
	
- ### super
	- Refers to the **parent class** of the current object.
	- Can be used to **call parent class methods or constructors**.
	- **Example:** `super();`
	
- ### package
	- Defines a **namespace** for classes.
	- Helps organize code and avoid naming conflicts.
	
- ### import
	- Allows **using classes from other packages**.

---



