C++ basics and Object-Oriented Programming

What are the different data types in C++?

![WhatsApp Image 2024-11-11 at 21 39 05_5f7fa249](https://github.com/user-attachments/assets/8aead28c-8e5a-4136-a2a1-085376b75439)


What are access modifiers?
access modifer how and where a member of a class can be accessed within or out side of class

private can be accessed from outside classes using friend function and friend classes.

protected : accessible within the class and drived class.

![WhatsApp Image 2024-11-11 at 22 00 36_82640fa0](https://github.com/user-attachments/assets/da299618-0be5-46c2-af37-8dcddd05b16d)

Explain object oriented programming. What is inheritance ? What are the types of inheritance?
### Object-Oriented Programming (OOP)
Object-Oriented Programming (OOP) is a programming paradigm that organizes software design around objects, which represent real-world entities or concepts. OOP focuses on encapsulating data and functions into a single unit called an object and defining the relationships between these objects. This approach promotes modularity, code reuse, and better organization.

Key principles of OOP include:

1. **Encapsulation**: Bundling data (attributes) and methods (functions) that operate on that data within a single unit, or class. Encapsulation also restricts access to certain details of an object, exposing only the necessary parts through methods.

2. **Abstraction**: Hiding complex implementation details and exposing only essential features. Abstraction simplifies interactions with objects, letting the user work with a clean, simplified interface.

3. **Inheritance**: A way to create new classes based on existing classes, inheriting their attributes and behaviors while adding new ones or modifying existing ones.

4. **Polymorphism**: Allowing objects of different classes to be treated as objects of a common base class. Polymorphism enables methods to operate differently based on the actual object being referenced.

---

### What is Inheritance?
Inheritance is an OOP feature that allows a class (called the **derived** or **subclass**) to inherit attributes and behaviors (data members and methods) from another class (called the **base** or **superclass**). This promotes code reuse and hierarchical classification. 

- **Purpose**: Inheritance allows us to define a hierarchy for classes, so that child classes can inherit common functionality from parent classes while also introducing unique features.
- **Example**: A class `Vehicle` might have attributes like `speed` and methods like `move()`. `Car` and `Bike` classes can inherit from `Vehicle` and thus share the `speed` attribute and `move()` method while also having their own specific properties.

   ```cpp
   class Vehicle {
   public:
       void move() { cout << "Vehicle is moving" << endl; }
   };

   class Car : public Vehicle {
   public:
       void honk() { cout << "Car honks!" << endl; }
   };
   ```

In this example, `Car` inherits from `Vehicle`, so it can use the `move()` method while also defining its own method, `honk()`.

---

### Types of Inheritance in C++

1. **Single Inheritance**:
   - A derived class inherits from only one base class.
   - **Example**: A `Car` class inheriting from a `Vehicle` class.

     ```cpp
     class Vehicle { /*...*/ };
     class Car : public Vehicle { /*...*/ };
     ```

2. **Multiple Inheritance**:
   - A derived class inherits from more than one base class.
   - **Example**: A `StudentAthlete` class that inherits from both `Student` and `Athlete` classes.

     ```cpp
     class Student { /*...*/ };
     class Athlete { /*...*/ };
     class StudentAthlete : public Student, public Athlete { /*...*/ };
     ```

3. **Hierarchical Inheritance**:
   - Multiple derived classes inherit from a single base class.
   - **Example**: `Car` and `Bike` both inherit from `Vehicle`.

     ```cpp
     class Vehicle { /*...*/ };
     class Car : public Vehicle { /*...*/ };
     class Bike : public Vehicle { /*...*/ };
     ```

4. **Multilevel Inheritance**:
   - A chain of inheritance where a class is derived from another derived class.
   - **Example**: `ElectricCar` inherits from `Car`, which inherits from `Vehicle`.

     ```cpp
     class Vehicle { /*...*/ };
     class Car : public Vehicle { /*...*/ };
     class ElectricCar : public Car { /*...*/ };
     ```

5. **Hybrid Inheritance**:
   - A combination of two or more types of inheritance, often used in complex scenarios.
   - **Example**: A class might inherit attributes from multiple classes that are themselves derived from a common base class.

   ```cpp
   class Vehicle { /*...*/ };
   class Car : public Vehicle { /*...*/ };
   class Boat : public Vehicle { /*...*/ };
   class AmphibiousVehicle : public Car, public Boat { /*...*/ };
   ```

   Hybrid inheritance can lead to a **diamond problem** if the base class is inherited by multiple paths. In C++, this can be solved with **virtual inheritance**.

---

### Key Points of Inheritance

- **“is-a” Relationship**: Inheritance represents an "is-a" relationship, meaning a derived class is a type of its base class (e.g., `Car` is a `Vehicle`).
- **Access Control**: Inherited members of the base class can be controlled with access specifiers (`public`, `protected`, `private`), determining the visibility and accessibility of inherited members.
- **Constructors and Destructors**: Constructors of the base class are called before the derived class constructor, and destructors are called in the reverse order to ensure proper resource management.
- **Polymorphism**: With inheritance, polymorphism allows overriding of base class methods in the derived class, allowing dynamic behavior.

Inheritance is fundamental in OOP as it allows us to define common behaviors in a base class, extend them in derived classes, and reuse code effectively.

Object-Oriented Programming (OOP) is a programming paradigm centered around the concept of "objects," which are instances of classes. OOP provides a structured way to organize software, making it modular, reusable, and easier to maintain. Key principles of OOP include:

1. **Encapsulation**: Bundling data (attributes) and methods (functions) that manipulate the data into a single unit (class). Access to data can be restricted using access specifiers.
2. **Abstraction**: Hiding complex implementation details and exposing only essential features through a clear interface.
3. **Inheritance**: A mechanism that allows one class to inherit properties and behaviors from another class, enabling code reuse and hierarchical classification.
4. **Polymorphism**: The ability to present the same interface for different data types, enabling functions to process objects differently based on their data type or class.

---

### What is Inheritance?
Inheritance is an OOP concept that allows one class (the **derived** or **subclass**) to inherit properties and behaviors (data members and methods) from another class (the **base** or **superclass**). This allows the subclass to reuse code from the superclass, extending or modifying it as needed.

- **Purpose**: Inheritance helps create a hierarchical structure and promotes code reuse, making it easier to maintain and scale software.
- **Example**: In a system with a base class `Animal`, specific types of animals like `Dog` and `Cat` can be derived classes. They inherit common characteristics from `Animal` but can also have unique properties and behaviors.

   ```cpp
   class Animal {
   public:
       void eat() { cout << "Eating..." << endl; }
   };

   class Dog : public Animal {
   public:
       void bark() { cout << "Barking..." << endl; }
   };
   ```

### Types of Inheritance in C++

1. **Single Inheritance**:
   - A derived class inherits from a single base class.
   - **Example**: `Dog` inherits from `Animal`.

     ```cpp
     class Animal { /*...*/ };
     class Dog : public Animal { /*...*/ };
     ```

2. **Multiple Inheritance**:
   - A derived class inherits from more than one base class.
   - **Example**: `StudentAthlete` inherits from both `Student` and `Athlete`.

     ```cpp
     class Student { /*...*/ };
     class Athlete { /*...*/ };
     class StudentAthlete : public Student, public Athlete { /*...*/ };
     ```

3. **Hierarchical Inheritance**:
   - Multiple derived classes inherit from a single base class.
   - **Example**: `Dog` and `Cat` both inherit from `Animal`.

     ```cpp
     class Animal { /*...*/ };
     class Dog : public Animal { /*...*/ };
     class Cat : public Animal { /*...*/ };
     ```

4. **Multilevel Inheritance**:
   - A class is derived from another class, which is also derived from another class, forming a chain.
   - **Example**: `BabyDog` inherits from `Dog`, which inherits from `Animal`.

     ```cpp
     class Animal { /*...*/ };
     class Dog : public Animal { /*...*/ };
     class BabyDog : public Dog { /*...*/ };
     ```

5. **Hybrid (or Virtual) Inheritance**:
   - A combination of two or more types of inheritance.
   - Often used in complex systems where a class might need to inherit from multiple classes.
   - **Example**: `AmphibiousVehicle` inherits properties from both `Car` and `Boat`, combining multiple inheritance types.

     ```cpp
     class Car { /*...*/ };
     class Boat { /*...*/ };
     class AmphibiousVehicle : public Car, public Boat { /*...*/ };
     ```

---

### Key Points of Inheritance

- Inheritance establishes an **"is-a"** relationship. For example, a `Dog` **is an** `Animal`.
- Access specifiers (`public`, `protected`, and `private`) control visibility of base class members in derived classes.
- **Polymorphism** often relies on inheritance, where derived classes override base class methods to provide specific behaviors.
- C++ also supports **virtual inheritance** to avoid issues like the **diamond problem** in multiple inheritance, where ambiguity arises if multiple paths lead back to the same base class.

Inheritance helps in structuring code in a modular, logical way, promoting reusability, reducing redundancy, and making the codebase easier to understand and maintain.
Explain and code multiple level inheritance. In multiple inheritance, does the order of defining base class matter.
What is polymorphism?
Give example of Operator Overloading
What is the difference between a struct and a class?
What is virtual function? Explain virtual tables and virtual pointers.
What is the difference between malloc and calloc?
What is dynamic memory allocation?
Operating Systems

What is paging and page fault ? What is virtual memory ?
What is multithreading ? What is the difference between process and thread ?
What are the various scheduling algorithms ? Why are scheduling algorithms used ?
What is deadlock ? What are mutex and semaphore ?
DBMS: The interviewer asked me if I know database management system. I told her that I have worked with databases but have not done a formal course as I am not from CS . She then told me it is fine and asked me about Web Services instead.

Web Services

What is client server model ?
What are the different types of http protocols?
What is a REST API ? What are the different methods?
Algorithms

Given a vector of strings, return the index of element that has maximum number of vowels. Asked me to code the brute force approach and discussed the optimized solution.
