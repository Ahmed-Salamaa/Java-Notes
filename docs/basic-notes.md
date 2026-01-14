
# Java

Java is called ‘Platform Independent Language’ as it primarily works on the principle of ‘compile once, run everywhere’.

```java
System.out.println("Hello World!");
```

---

# Take Input

```java
import java.util.Scanner;  // Import the Scanner class

Scanner myObj = new Scanner(System.in);  // Create a Scanner object
String userName = myObj.nextLine();  // Read user input
```

---
# Input Types

> **In the example above, we used the `nextLine()` method, which is used to read Strings. To read other types, look at the table below:**

| Method          | Description                           |
| --------------- | ------------------------------------- |
| `nextBoolean()` | Reads a `boolean` value from the user |
| `nextByte()`    | Reads a `byte` value from the user    |
| `nextDouble()`  | Reads a `double` value from the user  |
| `nextFloat()`   | Reads a `float` value from the user   |
| `nextInt()`     | Reads a `int` value from the user     |
| `nextLine()`    | Reads a `String` value from the user  |
| `nextLong()`    | Reads a `long` value from the user    |
| `nextShort()`   | Reads a `short` value from the user   |

---
# Java Comments

- ### Single-line Comments
		Single-line comments start with two forward slashes `//`.

- ### Multi-line Comments
		Multi-line comments start with `/*` and ends with `*/`.

---

# Java Data Types

### The var Keyword

The `var` keyword lets the compiler automatically detect the type of a variable based on the value you assign to it.

---
### Primitive Data Types

A **primitive data type** defines the type of a variable and the kind of values it can store.  
Java provides **eight built-in primitive data types**:

| Data Type | Description                               | Range (Power of 2) | Example                 |
| --------- | ----------------------------------------- | ------------------ | ----------------------- |
| `byte`    | Stores very small whole numbers           | −2⁷ to 2⁷          | `byte b = 100;`         |
| `short`   | Stores small whole numbers                | −2¹⁵ to 2¹⁵        | `short s = 30000;`      |
| `int`     | Stores standard whole numbers             | −2³¹ to 2³¹        | `int x = 100000;`       |
| `long`    | Stores very large whole numbers           | −2⁶³ to 2⁶³        | `long l = 1000000000L;` |
| `float`   | Stores decimal numbers (single precision) |                    | `float f = 3.14f;`      |
| `double`  | Stores decimal numbers (double precision) |                    | `double d = 3.141592;`  |
| `boolean` | Stores logical values                     | `true` or `false`  | `boolean flag = true;`  |
| `char`    | Stores a single character (Unicode)       | 0 to 2¹⁶           | `char c = 'A';`         |

---
### Non-Primitive Data Types

* Non-primitive data types are called **reference types** because they refer to objects.
	- Primitive types in Java are predefined and built into the language, while non-primitive types are created by the programmer (except for `String`).
	- Non-primitive types can be used to call methods to perform certain operations, whereas primitive types cannot.
	- Primitive types start with a lowercase letter (like `int`), while non-primitive types typically starts with an uppercase letter (like `String`).
	- Primitive types always hold a value, whereas non-primitive types can be `null`.
	- Variables **store a reference (memory address)**, not the actual object.

| Data Type   | Description                                    | Example                      |
| ----------- | ---------------------------------------------- | ---------------------------- |
| `String`    | Stores a sequence of characters                | `String name = "Ahmed";`     |
| `Array`     | Stores multiple values of the same type        | `int[] arr = {1, 2, 3};`     |
| `Class`     | Blueprint for creating objects                 | `class Student { }`          |
| `Object`    | Parent class of all classes in Java            | `Object obj = new Object();` |
| `Interface` | Defines a contract that classes must implement | `interface Animal { }`       |

---
### Primitive vs Non-Primitive Data Types

|Feature|Primitive|Non-Primitive|
|---|---|---|
|Stored value|Actual value|Reference to object|
|Predefined|Yes|No (except `String`)|
|Can call methods|No|Yes|
|Can be `null`|No|Yes|
|Naming style|Lowercase|Uppercase|

---
### Immutable Data Types

#### What is an Immutable Object?

An **immutable object** is an object whose state **cannot be changed after creation**.

---
#### Immutable vs Mutable Comparison

| Feature      | Immutable Objects      | Mutable Objects                  |
| ------------ | ---------------------- | -------------------------------- |
| State change | ❌ Not allowed          | ✅ Allowed                        |
| Thread-safe  | ✅ Yes                  | ❌ No (needs synchronization)     |
| Performance  | ❌ More objects created | ✅ Fewer objects                  |
| Security     | ✅ High                 | ❌ Lower                          |
| Examples     | `String`,<br>`Integer` | `StringBuilder`, <br>`ArrayList` |

---
#### Common Immutable Data Types

|Data Type|Immutable|Reason|
|---|---|---|
|`String`|✅ Yes|Any modification creates a new object|
|`Integer`|✅ Yes|Value cannot be changed|
|`Long`|✅ Yes|Wrapper class, immutable|
|`Double`|✅ Yes|Wrapper class, immutable|
|`Float`|✅ Yes|Wrapper class, immutable|
|`Boolean`|✅ Yes|Wrapper class, immutable|
|`Character`|✅ Yes|Wrapper class, immutable|
|`BigInteger`|✅ Yes|Operations return new objects|
|`BigDecimal`|✅ Yes|Operations return new objects|

---

#### Example: `String` (Immutable)

```java
String s1 = "Hello";
s1.concat(" World");
System.out.println(s1); // Output: Hello
```

> ✔ `s1` is unchanged because `String` is immutable.

---
#### Example: `StringBuilder` (Mutable)

```java
StringBuilder sb = new StringBuilder("Hello");
sb.append(" World");
System.out.println(sb); // Output: Hello World
```

> ✔ `StringBuilder` is mutable.

---

#### Why Java Uses Immutable Objects?

> - Thread safety
> - Better security
> - Safe sharing between methods
> - Reliable hashing (used in `HashMap` keys)

---

#### How to Create Your Own Immutable Class?

> Rules:
> 1. Make class `final`
> 2. Make fields `private final`
> 3. No setter methods
> 4. Return copies of mutable fields

---
# Type Casting

In Java, there are two main types of casting:

- **Widening Casting** (automatic) - converting a smaller type to a larger type size  
    `byte` -> `short` -> `char` -> `int` -> `long` -> `float` -> `double`    

- **Narrowing Casting** (manual) - converting a larger type to a smaller type size  
    `double` -> `float` -> `long` -> `int` -> `char` -> `short` -> `byte`
    
```java
	double myDouble = 9.78d;
	int myInt = (int) myDouble; // Manual casting: double to int
	
	System.out.println(myDouble); // Outputs 9.78
	System.out.println(myInt);    // Outputs 9
```

> From Double to Integer -> Trancate the float part
> From Big Integer to Small Interget -> truncat the `MSB`

---
# Strings - Special Characters

Because strings must be written within quotes, Java will misunderstand this string, and generate an error:

```java
String txt = "We are the so-called "Vikings" from the north.";
```

The solution to avoid this problem, is to use the **backslash escape character**.

The backslash (`\`) escape character turns special characters into string characters:

| Escape character | Result          |
| ---------------- | --------------- |
| `\'`             | '               |
| `\"`             | "               |
| `\\`             | \               |
| `\n`             | New Line        |
| `\t`             | Tab             |
| `\b`             | Backspace       |
| `\r`             | Carriage Return |
| `\f`             | Form Feed       |

---
# Java Arrays

Arrays are used to store multiple values in a single variable, instead of declaring separate variables for each value.

To declare an array, define the variable type with **square brackets** `[ ]` :

```java
String[] cars;
cars = new String[]{"Volvo", "BMW", "Ford", "Mazda"};

for (int i = 0; i < cars.length; i++)
	System.out.println(cars[i]);
```

```java
String[] cars = {"Volvo", "BMW", "Ford", "Mazda"};

for (String car : cars)
	System.out.println(car);
```

```java
int[][] myNumbers = { {1, 4, 2}, {3, 6, 8, 5, 2} };

for (int[] row : myNumbers) 
{
    for (int num : row) 
    {
	System.out.println(num);
    }
}
```

---
# Java Methods

In Java, **all method arguments are passed by value**, but the behavior depends on whether the argument is a **primitive type** or an **object reference**:

1. **Primitive types** (`int`, `double`, `boolean`, etc.):
    
    - The method receives a **copy of the value**.
    - Changes inside the method **do not affect the original variable**.
    
```java
    void modify(int x) 
    {
        x = x + 10;
    }
    
    int a = 5;
    modify(a);
    System.out.println(a); // Output: 5
```
    
2. **Objects** (`String`, arrays, custom objects, etc.):
    
    - The method receives a **copy of the reference** to the object.
    - Changes to the object’s **internal state** affect the original object, but reassigning the reference itself does **not**.
    
```java
    void modifyArray(int[] arr) {
        arr[0] = 10;       // Changes the original array
        arr = new int[]{5}; // Reassigning has no effect outside
    }
    
    int[] nums = {1, 2, 3};
    modifyArray(nums);
    System.out.println(nums[0]); // Output: 10
```

---

# Division by Zero in Java


## Integers

Firstly, for integers, things are pretty straightforward. **Dividing an integer by zero will result in an _ArithmeticException_:**

```java
assertThrows(ArithmeticException.class, () -> {
    int result = 12 / 0;
});
```

## Floating Point Types

However, when dealing **with floating-point numbers_,_ an exception won’t be thrown**:

```java
assertDoesNotThrow(() -> {
    float result = 12f / 0;
});
```

In order to handle cases like these, Java uses some special numeric values that can represent the results of such an operation: `NaN`, `POSITIVE_INFINITY`, and `NEGATIVE_INFINITY` .

### NaN

Let’s start by **dividing floating-point zero values by zero**:

```java
assertEquals(Float.NaN, 0f / 0);
assertEquals(Double.NaN, 0d / 0);
```

The result in these cases is [_NaN_](https://www.baeldung.com/java-not-a-number) (not a number).

### Infinity

Next, let’s **divide some non-zero values by zero**:

```java
assertEquals(Float.POSITIVE_INFINITY, 12f / 0);
assertEquals(Double.POSITIVE_INFINITY, 12d / 0);
assertEquals(Float.NEGATIVE_INFINITY, -12f / 0);
assertEquals(Double.NEGATIVE_INFINITY, -12d / 0);
```

As we can see, the result is _INFINITY,_ with the sign depending on the sign of the operands.

Moreover, we can also use the concept of negative zero in order to get to _NEGATIVE_INFINITY_:

```java
assertEquals(Float.NEGATIVE_INFINITY, 12f / -0f);
assertEquals(Double.NEGATIVE_INFINITY, 12f / -0f);
```

### Memory Representation[](https://www.baeldung.com/java-division-by-zero#3-memory-representation)

So, why does integer division by zero throw an exception, while floating-point division by zero does not?

Let’s look at this from a memory representation perspective. **For integers, there is no bit pattern that can be used to store the result** of such an operation, while **floating-point numbers have values like _NaN_ or _INFINITY_ to be used in cases like these.**

Now, let’s consider the binary representation of a float as 
> SEEEEEEE EFFFFFFF FFFFFFFF FFFFFFFF 

with one bit (S) for the sign, 8 bits (E) for the exponent, and the rest (F) for the mantissa.

In each of the three values _NaN_, _POSITIVE_INFINITY,_ and NEGATIVE_INFINITY, **all bits in the exponent part are set to 1.**

_INFINITY_ has the mantissa bits all set to 0, while _NaN_ has a non-zero mantissa:

```java
assertEquals(Float.POSITIVE_INFINITY, Float.intBitsToFloat(0b01111111100000000000000000000000));
assertEquals(Float.NEGATIVE_INFINITY, Float.intBitsToFloat(0b11111111100000000000000000000000));
assertEquals(Float.NaN, Float.intBitsToFloat(0b11111111100000010000000000000000));
assertEquals(Float.NaN, Float.intBitsToFloat(0b11111111100000011000000000100000));
```