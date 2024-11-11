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

**Explain and code multiple level inheritance. In multiple inheritance, does the order of defining base class matter.**

### **Multiple Level Inheritance in C++**
In **multilevel inheritance**, a class is derived from another derived class, creating a chain of inheritance. This means that a class inherits from another class, which in turn inherits from yet another class. It forms a hierarchy where the base class is at the top and the derived classes are below it.

#### **Example of Multilevel Inheritance**
Consider the following example where a `Grandparent` class is the base class, the `Parent` class is derived from `Grandparent`, and the `Child` class is derived from `Parent`.

```cpp
#include <iostream>
using namespace std;

// Base class
class Grandparent {
public:
    void grandparentMethod() {
        cout << "This is a method in the Grandparent class." << endl;
    }
};

// Derived class from Grandparent
class Parent : public Grandparent {
public:
    void parentMethod() {
        cout << "This is a method in the Parent class." << endl;
    }
};

// Derived class from Parent
class Child : public Parent {
public:
    void childMethod() {
        cout << "This is a method in the Child class." << endl;
    }
};

int main() {
    // Creating an object of Child class
    Child childObj;
    
    // Calling methods from all three classes
    childObj.grandparentMethod();  // Inherited from Grandparent
    childObj.parentMethod();       // Inherited from Parent
    childObj.childMethod();        // Defined in Child class

    return 0;
}
```

### **Explanation of the Code:**

1. **Grandparent class**: The base class with the method `grandparentMethod()`.
2. **Parent class**: Inherits from `Grandparent` and adds the method `parentMethod()`.
3. **Child class**: Inherits from `Parent`, and adds its own method `childMethod()`.

In the `main()` function, we create an object of the `Child` class, and this object can access methods from all three classes because of the multilevel inheritance. The methods `grandparentMethod()`, `parentMethod()`, and `childMethod()` are all available.

### **Does the Order of Defining Base Classes Matter in Multiple Inheritance?**
In **multilevel inheritance**, the order in which the base classes are defined does not matter. The only order that matters is the sequence in which the classes are inherited. For instance, the `Parent` class must inherit from the `Grandparent` class, and the `Child` class must inherit from the `Parent` class.

However, **in multiple inheritance** (where a class inherits from more than one base class), **the order of base classes does matter**. The order determines which base class constructors are called first and how ambiguities are resolved in case of method name conflicts.

#### **Example of Multiple Inheritance:**
```cpp
#include <iostream>
using namespace std;

// Base class 1
class Base1 {
public:
    void methodBase1() {
        cout << "Method of Base1" << endl;
    }
};

// Base class 2
class Base2 {
public:
    void methodBase2() {
        cout << "Method of Base2" << endl;
    }
};

// Derived class from both Base1 and Base2
class Derived : public Base1, public Base2 {
public:
    void methodDerived() {
        cout << "Method of Derived class" << endl;
    }
};

int main() {
    Derived d;
    d.methodBase1();    // Inherited from Base1
    d.methodBase2();    // Inherited from Base2
    d.methodDerived();  // Defined in Derived class
    return 0;
}
```

### **Explanation:**
In this example, the `Derived` class is inheriting from two base classes: `Base1` and `Base2`. Both `Base1` and `Base2` have their own methods (`methodBase1` and `methodBase2`), and the `Derived` class inherits both of these methods. 

#### **Order in Multiple Inheritance**
In multiple inheritance, the order in which base classes are defined affects the initialization and method lookup order. For example, if there is a method name conflict between base classes, the order determines which base class’s method gets called.

Let’s illustrate this with an example of method overriding or ambiguity in case of multiple inheritance:

```cpp
#include <iostream>
using namespace std;

class Base1 {
public:
    void display() {
        cout << "Display method from Base1" << endl;
    }
};

class Base2 {
public:
    void display() {
        cout << "Display method from Base2" << endl;
    }
};

// Derived class from both Base1 and Base2
class Derived : public Base1, public Base2 {
public:
    void show() {
        cout << "Show method from Derived class" << endl;
    }
};

int main() {
    Derived d;
    // Ambiguity: Which display() to call?
    d.Base1::display();  // Explicitly calling Base1's display method
    d.Base2::display();  // Explicitly calling Base2's display method
    d.show();            // Calling method from Derived class
    return 0;
}
```

### **Explanation of the Ambiguity:**
- If the `Derived` class inherits methods from `Base1` and `Base2` that have the same name (`display()`), there would be ambiguity about which `display()` method to call.
- To resolve this ambiguity, we explicitly specify which base class's `display()` method to call using the scope resolution operator (`Base1::display()` or `Base2::display()`).

### **Conclusion:**
- **In multilevel inheritance**, the order of base classes does not matter because each derived class is inheriting from a single base class in the chain.
- **In multiple inheritance**, the order of base classes does matter, particularly when there are method name conflicts or ambiguities. The order affects constructor initialization and how methods are resolved during execution.

** What is polymorphism?**

### **Polymorphism in Object-Oriented Programming (OOP)**

**Polymorphism** is one of the four fundamental principles of Object-Oriented Programming (OOP), alongside **encapsulation**, **inheritance**, and **abstraction**. It literally means **"many forms"** and refers to the ability of different objects to respond to the same message (method call) in different ways. 

In simpler terms, polymorphism allows one interface to be used for a general class of actions, making it easier to scale and maintain code.

There are two main types of polymorphism in OOP:

1. **Compile-time Polymorphism (Static Polymorphism)** 
2. **Run-time Polymorphism (Dynamic Polymorphism)**

### 1. **Compile-time Polymorphism (Static Polymorphism)**

This is achieved through **method overloading** and **operator overloading**. The decision about which method to call is made at compile time, and the method to execute is chosen based on the number or type of parameters passed to the method.

- **Method Overloading**: This occurs when multiple methods in the same class have the same name but differ in the number or types of parameters.

#### Example of Method Overloading:
```cpp
#include <iostream>
using namespace std;

class Calculator {
public:
    // Overloaded method for addition (int)
    int add(int a, int b) {
        return a + b;
    }

    // Overloaded method for addition (double)
    double add(double a, double b) {
        return a + b;
    }
};

int main() {
    Calculator calc;
    
    // Calls the int version of add()
    cout << "Sum of integers: " << calc.add(5, 3) << endl;
    
    // Calls the double version of add()
    cout << "Sum of doubles: " << calc.add(5.5, 3.3) << endl;

    return 0;
}
```
**Output**:
```
Sum of integers: 8
Sum of doubles: 8.8
```

Here, the method `add` is overloaded to handle both integer and double data types. The correct version is called based on the argument type, demonstrating **compile-time polymorphism**.

---

### 2. **Run-time Polymorphism (Dynamic Polymorphism)**

This occurs when the method that gets called is determined at **runtime**, and is typically achieved through **method overriding** in the context of **inheritance**.

- **Method Overriding**: When a subclass provides a specific implementation of a method that is already defined in its superclass. The method in the subclass overrides the method in the superclass.

In **dynamic polymorphism**, you need to use **pointers or references** to the base class and ensure the base class method is declared as **virtual**.

#### Example of Method Overriding (Run-time Polymorphism):
```cpp
#include <iostream>
using namespace std;

// Base class
class Animal {
public:
    virtual void sound() {  // Virtual function to allow overriding
        cout << "Some animal sound" << endl;
    }
};

// Derived class
class Dog : public Animal {
public:
    void sound() override {  // Overriding the sound method
        cout << "Woof Woof!" << endl;
    }
};

// Derived class
class Cat : public Animal {
public:
    void sound() override {  // Overriding the sound method
        cout << "Meow!" << endl;
    }
};

int main() {
    Animal* animal;
    
    Dog dog;
    Cat cat;

    // Base class pointer refers to derived class object
    animal = &dog;
    animal->sound();  // Calls Dog's sound

    animal = &cat;
    animal->sound();  // Calls Cat's sound

    return 0;
}
```

**Output**:
```
Woof Woof!
Meow!
```

In this case, the base class pointer `animal` can point to both `Dog` and `Cat` objects. Since the `sound()` method is virtual, the appropriate method (from the derived class) is called at runtime based on the actual type of the object (`dog` or `cat`), demonstrating **run-time polymorphism**.

---

### **Key Differences Between Compile-time and Run-time Polymorphism**

| Aspect                          | **Compile-time Polymorphism**               | **Run-time Polymorphism**                   |
|----------------------------------|--------------------------------------------|--------------------------------------------|
| **Occurs during**               | Compile time                               | Runtime                                    |
| **Achieved by**                 | Method Overloading, Operator Overloading   | Method Overriding, Virtual functions       |
| **Method Resolution**           | Resolved by the compiler                  | Resolved by the runtime environment (JVM, etc.) |
| **Performance**                 | More efficient, faster                    | Slightly slower due to dynamic dispatch    |
| **Type of Binding**             | Static binding                            | Dynamic binding                            |

---

### **Advantages of Polymorphism**:
- **Code Reusability**: You can define methods in the base class and override them in derived classes. This leads to cleaner, more reusable code.
- **Extensibility**: New classes can be added without modifying the existing code. This makes the system more flexible.
- **Simplified Code**: Polymorphism allows for simpler code because it provides a uniform interface to different types of objects.

---

### **Conclusion**:
Polymorphism is a key feature of OOP that allows objects to be treated as instances of their parent class while retaining their unique behaviors. It enhances flexibility, reusability, and scalability of code. By using **method overloading** (compile-time polymorphism) and **method overriding** (run-time polymorphism), polymorphism enables objects of different classes to respond to the same method call in a way appropriate to their class type.

Give example of Operator Overloading

### **Operator Overloading in C++**

**Operator overloading** is a feature in C++ that allows you to define custom behavior for operators (like `+`, `-`, `*`, etc.) when they are applied to objects of user-defined classes. By overloading an operator, you can make it work in a way that is appropriate for your class, just like built-in types (e.g., integers or floats).

### **Example of Operator Overloading**

Let's take an example where we overload the `+` operator to add two objects of a custom `Complex` class (representing complex numbers).

#### Code:

```cpp
#include <iostream>
using namespace std;

// Define a class for Complex Numbers
class Complex {
private:
    float real;
    float imag;

public:
    // Constructor to initialize a complex number
    Complex(float r, float i) : real(r), imag(i) {}

    // Overload the '+' operator to add two Complex numbers
    Complex operator+(const Complex& other) {
        // Add real and imaginary parts separately
        return Complex(real + other.real, imag + other.imag);
    }

    // Function to display the complex number
    void display() {
        cout << real << " + " << imag << "i" << endl;
    }
};

int main() {
    // Create two Complex number objects
    Complex num1(3.5, 2.5);
    Complex num2(1.5, 3.5);

    // Use overloaded '+' operator to add the complex numbers
    Complex result = num1 + num2;

    // Display the result
    cout << "Result of adding two complex numbers: ";
    result.display();

    return 0;
}
```

#### **Explanation**:
1. **Complex Class**: 
   - It has two data members: `real` and `imag` representing the real and imaginary parts of a complex number.
   - The constructor initializes these values.

2. **Operator Overloading**: 
   - The `operator+` is overloaded to allow the addition of two `Complex` objects. It adds the real parts and the imaginary parts of two complex numbers separately and returns a new `Complex` object.

3. **Main Function**:
   - We create two `Complex` objects, `num1` and `num2`.
   - The overloaded `+` operator is used to add `num1` and `num2`, and the result is stored in the `result` object.
   - The `display()` method is called to print the result.

#### **Output**:
```
Result of adding two complex numbers: 5 + 6i
```

### **Key Points**:
- **Operator overloading** allows you to specify custom behavior for operators when applied to objects of your own class.
- You can overload many operators, but not all (e.g., you cannot overload the assignment operator `=` in C++).
- Overloading operators like `+`, `-`, `*`, etc., enables you to write more intuitive and readable code, especially when dealing with custom data types.

### **Conclusion**:
In this example, we've overloaded the `+` operator to add two complex numbers in a way that is more natural and meaningful for the `Complex` class. Operator overloading improves code readability and allows you to define custom operations for objects of your classes.


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

Round 3: This round was taken by a really experienced engineer and was a system design + HR round.

System Design

Design an online banking management system. Low Level System Design and Object Oriented Programming was expected. The interviewer also expected me to take care of concurrency issues.
HR Type Questions

Talk about your internships. Asked me in detail about a specific internship.
Talk about your favourite project.
Asked me to give an instance of when I had worked in a team and what responsibilities I had handled.
6 students were selected finally. 4 were offered internship + full-time and 2 were offered 6 month internship.

Preparation: Morgan Stanley Archives from GeeksforGeeks. (Very important. Got a good idea of what sort of questions will be asked. OOPs and C++ from https://www.studytonight.com/cpp/

Operating Systems from GeeksforGeeks and StudyTonight. I studied only the important topics that I observed were being asked frequently in Morgan Stanley. They are

Process vs Thread
Why is thread a lightweight process and process heavy
Multitasking
Multithreading.
Simple C++ program to implement threads
Deadlocks
Mutex and Semaphore
Virtual Memory
Thrashing
Page Replacement
Scheduling Algorithms
LRU Cache
