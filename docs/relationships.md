# Association

Association is the cardinal concept in object-oriented programming that describes the relationship between two independent classes. Association can be viewed as describing a "uses-a" relationship where an object uses, or in any way interacts with, another object. Association may be either unidirectional or bidirectional and may exist in several forms, such as one-to-one, one-to-many, many-to-one, and many-to-many.

## Types of Association

- ****Unidirectional Association****: This association is the one in which one class is aware and associated with another class; the reverse is not true. For example, the Student class can be associated with the LibraryCard class, for the association where the student has a library card; a LibraryCard does not need to 'know about' a Student.
- ****Bidirectional Association****: In this type of association, the classes are aware of each other and interact with one another. For example, a Teacher class and a Classroom class may be associated bidirectionally; there would be a teacher assigned to a classroom, and a classroom would know to which teacher it is assigned.

## Association Example:

```java

// Java Program to illustrate the
// Concept of Association

// Importing required classes
import java.io.*;
import java.util.*;

// Class 1
// Bank class
class Bank {

    // Attributes of bank
    private String bankName;
    private Set<Employee> employees;
  
    // Constructor of Bank class
    public Bank(String bankName)
    {
        this.bankName = bankName;
    }

    // Method of Bank class
    public String getBankName()
    {
        // Returning name of bank
        return this.bankName;
    }

    public void setEmployees(Set<Employee> employees)
    {
        this.employees = employees;
    }
  
    public Set<Employee> getEmployees()
    {
        return this.employees;
    }
}

// Class 2
// Employee class
class Employee {
  
    // Attributes of employee
    private String name;
  
    // Constructor of Employee class
    public Employee(String name)
    {
        // this keyword refers to current instance
        this.name = name;
    }

    // Method of Employee class
    public String getEmployeeName()
    {
        // returning the name of employee
        return this.name;
    }
}

// Class 3
// Association between both the
// classes in main method
class AssociationExample {

    // Main driver method
    public static void main(String[] args)
    {
        // Creating Employee objects
        Employee emp1 = new Employee("Ridhi");
          Employee emp2 = new Employee("Vijay");
        
          // adding the employees to a set
        Set<Employee> employees = new HashSet<>();
        employees.add(emp1);
          employees.add(emp2);

          // Creating a Bank object
          Bank bank = new Bank("ICICI");
      
          // setting the employees for the Bank object
        bank.setEmployees(employees);
        
          // traversing and displaying the bank employees 
          for (Employee emp : bank.getEmployees()) {
              System.out.println(emp.getEmployeeName()
                                 + " belongs to bank "
                                 + bank.getBankName());
        }
    }
}

```

### Explanation of the above Program:

In the above example, two separate classes Bank and Employee are associated through their Objects. Bank can have many employees, So, it is a one-to-many relationship.

![ relation explain]( https://media.geeksforgeeks.org/wp-content/uploads/Aggre.png )


# Aggregation

Aggregation is a relationship that comes under object-oriented programming, classifying an instance of a class as "has a." It's a form of association with weaker relationship strength, whereby the lifetime of the contained object (part) is not controlled based on the lifetime of the container object (whole). Concepts of aggregation are quite important for developing modular and reusable software components.

Aggregation is a type of association that represents a relationship where one class is a collection or container of another class. It depicts a "has-a" relationship, where the container object can exist independently of its contents, and the contained objects can exist independently of the container.

****t is a special form of Association where:****  

- It represents Has-A's relationship.
- It is a ****unidirectional association**** i.e. a one-way relationship. For example, a department can have students but vice versa is not possible and thus unidirectional in nature.
- In Aggregation, ****both entries can survive individually**** which means ending one entity will not affect the other entity.

## Aggregation Example:

```java

// Java program to illustrate
// Concept of Aggregation

// Importing required classes
import java.io.*;
import java.util.*;

// Class 1
// Student class
class Student {

    // Attributes of Student
    private String studentName;
    private int studentId;

    // Constructor of Student class
    public Student(String studentName, int studentId)
    {
        this.studentName = studentName;
        this.studentId = studentId;
    }

    public int getstudentId() { 
      return studentId; 
    }

    public String getstudentName() {
      return studentName; 
    }
}

// Class 2
// Department class 
// Department class contains list of Students
class Department {

    // Attributes of Department class
    private String deptName;
    private List<Student> students;

    // Constructor of Department class
    public Department(String deptName, List<Student> students)
    {
        this.deptName = deptName;
        this.students = students;
    }

    public List<Student> getStudents() {
      return students; 
    }

    public void addStudent(Student student)
    {
        students.add(student);
    }
}

// Class 3
// Institute class
// Institute class contains the list of Departments
class Institute {

    // Attributes of Institute
    private String instituteName;
    private List<Department> departments;

    // Constructor of Institute class
    public Institute(String instituteName,
                     List<Department> departments)
    {
        // This keyword refers to current instance itself
        this.instituteName = instituteName;
        this.departments = departments;
    }

    public void addDepartment(Department department)
    {
        departments.add(department);
    }

    // Method of Institute class
    // Counting total students in the institute
    public int getTotalStudentsInInstitute()
    {
        int noOfStudents = 0;
        List<Student> students = null;

        for (Department dept : departments) {
            students = dept.getStudents();

            for (Student s : students) {
                noOfStudents++;
            }
        }
        return noOfStudents;
    }
}

// Class 4
// main class
class AggregationExample {

    // main driver method
    public static void main(String[] args)
    {
        // Creating independent Student objects
        Student s1 = new Student("Parul", 1);
        Student s2 = new Student("Sachin", 2);
        Student s3 = new Student("Priya", 1);
        Student s4 = new Student("Rahul", 2);

        // Creating an list of CSE Students
        List<Student> cse_students = new ArrayList<Student>();
        cse_students.add(s1);
        cse_students.add(s2);

        // Creating an initial list of EE Students
        List<Student> ee_students = new ArrayList<Student>();
        ee_students.add(s3);
        ee_students.add(s4);

        // Creating Department object with a Students list
        // using Aggregation (Department "has" students)
        Department CSE = new Department("CSE", cse_students);
        Department EE = new Department("EE", ee_students);

        // Creating an initial list of Departments
        List<Department> departments = new ArrayList<Department>();
        departments.add(CSE);
        departments.add(EE);

        // Creating an Institute object with Departments list
        // using Aggregation (Institute "has" Departments)
        Institute institute = new Institute("BITS", departments);

        // Display message for better readability
        System.out.print("Total students in institute: ");

        // Calling method to get total number of students
        // in the institute and printing on console
        System.out.print(
            institute.getTotalStudentsInInstitute());
    }
}

```

### Explanation of the above Program:

In this example,

- There is an Institute which has no. of departments like CSE, EE. Every department has no. of students.
- So, we make an Institute class that has a reference to Object or no. of Objects (i.e. List of Objects) of the Department class.
- That means Institute class is associated with Department class through its Object(s).
- And Department class has also a reference to Object or Objects (i.e. List of Objects) of the Student class means it is associated with the Student class through its Object(s).

It represents a ****Has-A**** relationship. In the above example: Student ****Has-A**** name. Student ****Has-A**** ID. Department ****Has-A**** Students as depicted from the below media.

![]( https://media.geeksforgeeks.org/wp-content/uploads/Reference.png )


# Composition

Composition is a core concept in object-oriented programming that refers to the relationship "part-of" between classes. It is a stronger form of association in which the contained objects' lifecycle is strongly associated with the container object's lifecycle. The understanding of composition is crucial in the design of complex systems where objects of the system are composed of other objects.

****Composition**** is a type of association meaning one class "contains" another. This association can be said to be a "part-of" relationship and would denote that the contained object is strongly connected with the containing object, the whole. The parts cannot be without the whole.

Composition is a restricted form of Aggregation in which two entities are highly dependent on each other.  

- It represents ****part-of**** relationship.
- In composition, both entities are dependent on each other.
- When there is a composition between two entities, the composed object ****cannot exist**** without the other entity.


## Composition Example:

```java

// Java program to illustrate
// Concept of Composition

// Java program to illustrate the Concept of Composition

// Importing required classes

import java.io.*;
import java.util.*;

// Room class
class Room {

    private String roomName;

    public Room(String roomName) {
        this.roomName = roomName;
    }

    public String getRoomName() {
        return roomName;
    }
}

// House class
class House {

    private String houseName;
    private List<Room> rooms;

    public House(String houseName) {
        this.houseName = houseName;
        this.rooms = new ArrayList<>();
    }

    public void addRoom(Room room) {
        rooms.add(room);
    }

    public List<Room> getRooms() {
        return new ArrayList<>(rooms);
    }

    public int getTotalRooms() {
        return rooms.size();
    }
}

// Main class
class CompositionExample {

    public static void main(String[] args) {
        House house = new House("Dream House");

        house.addRoom(new Room("Living Room"));
        house.addRoom(new Room("Bedroom"));
        house.addRoom(new Room("Kitchen"));
        house.addRoom(new Room("Bathroom"));

        int r = house.getTotalRooms();
        System.out.println("Total Rooms: " + r);

        System.out.println("Room names: ");
        for (Room room : house.getRooms()) {
            System.out.println("- " + room.getRoomName());
        }
    }
}

```

### Explanation of the above Program:

In the above example, if the house is destroyed, its room also get destroyed this represents a complete composition relationship, where the room is the part of the house and the life cycle of room completely depends on the house.


# Difference Between Association, Aggregation and Composition


| Feature                   | Association                                                    | Aggregation                                                       | Composition                                                  |
| ------------------------- | -------------------------------------------------------------- | ----------------------------------------------------------------- | ------------------------------------------------------------ |
| Definition                | General relationship between two classes                       | A special form of association with a "has-a" relationship         | A stronger form of association with a "part-of" relationship |
| Dependency                | Classes are related but can exist independently                | Contained objects can exist independently of the container object | Contained objects cannot exist without the container object  |
| Lifecycle                 | Independent lifecycles                                         | Independent lifecycles                                            | Dependent lifecycles                                         |
| Ownership                 | No ownership implied                                           | Shared ownership                                                  | Exclusive ownership                                          |
| Strength                  | Weak                                                           | Moderate                                                          | Strong                                                       |
| Cardinality               | One-to-one, one-to-many, many-to-one, many-to-many             | One-to-one, one-to-many, many-to-one, many-to-many                | One-to-one, one-to-many                                      |
| Example                   | Teacher and Student                                            | Library and Books                                                 | Car and Engine                                               |
| Representation            | Uses a direct reference                                        | Uses a reference to the contained object(s)                       | Contains instances of the contained object(s)                |
| Illustrative Example Code | java class  <br>Teacher { private  <br>Student student;  <br>} | java class  <br>Library { private  <br>List<Book> books;  <br>}   | java class  <br>Car { private  <br>Engine engine;  <br>}     |