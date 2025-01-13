Why is the main method Public in Java?
We know that a method with a public access specifier can be accessed/invoked by anyone. Because the JVM must invoke the main method, it is public in Java. The JVM will not call main() if it is not public in Java.
 
Why is the main method Static and void in Java?
Because the main() method is static, JVM can call it without having to instantiate the class. This also saves memory that would have been wasted if the object had been declared only for the JVM to call the main() method.
Because the main method in Java does not return anything, its return type is void.
 
What is the meaning of “ import java.util.*;”?
It is a built-in package with a comparable set of classes, sub-packages, and interfaces. The * allows users to import a class from the existing package and use it as many times as they need in the programme



What is Method in Java?
A method is a segment of code that only executes when it is invoked. Parameters are data that can be passed into a method. Methods, often known as functions, are used to carry out specific tasks.
 
What do you mean by Recursion?
The technique of making a function call itself is known as recursion. This strategy allows you to break down complex difficulties into more minor, easier-to-solve problems.
 
How many types of Recursion are there?
There are two sorts of recursion: one in which a function calls itself from within itself, and the other in which multiple functions call each other mutually. The first is known as direct recursion, whereas the second is known as indirect recursion.
 
What is an Infinite Loop?
An infinite loop (also known as an endless loop) is a piece of code that continues indefinitely because it lacks a functional exit.
 
What is the critical difference between While and For loop in Java?
The difference between a for loop and a while loop is that in a for loop, the number of iterations to be performed is already known and is used to obtain a particular result, whereas, in a while loop, the command runs until a specific condition is met and the statement is proven untrue.
 
What do you mean by instance variable in Java?
When we have to instantiate an object, instance variables are created and are accessible to all constructors, methods, and blocks in the class.
In Java, instance variables are unique to each object created from a class. This means that when you create multiple objects from the same class, each object gets its own independent copy of the instance variables. As a result, modifying the instance variables of one object does not affect the values of the same instance variables in another object.

Why This Happens:

When you create an object using the new keyword, Java allocates separate memory for that object's instance variables.

Each object maintains its own state, which is represented by the values stored in its instance variables.


Example for Better Understanding

public class Person {
    // Instance variable
    private String name;

    // Constructor
    public Person(String name) {
        this.name = name;
    }

    // Method to change name
    public void setName(String name) {
        this.name = name;
    }

    // Method to display name
    public void display() {
        System.out.println("Name: " + name);
    }

    public static void main(String[] args) {
        Person person1 = new Person("Alice");
        Person person2 = new Person("Bob");

        person1.display();  // Output: Name: Alice
        person2.display();  // Output: Name: Bob

        // Change the name of person1
        person1.setName("Charlie");
        person1.display();  // Output: Name: Charlie
        person2.display();  // Output: Name: Bob
    }
}

In this example:

person1 and person2 are separate objects of the Person class.

They have separate copies of the name instance variable.

Changing person1's name to "Charlie" does not affect person2's name, which remains "Bob". This demonstrates that each object maintains its own copy of instance variables.


