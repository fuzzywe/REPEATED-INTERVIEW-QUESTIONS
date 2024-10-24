Why is the main method Public in Java?
We know that a method with a public access specifier can be accessed/invoked by anyone. Because the JVM must invoke the main method, it is public in Java. The JVM will not call main() if it is not public in Java.
 
Why is the main method Static and void in Java?
Because the main() method is static, JVM can call it without having to instantiate the class. This also saves memory that would have been wasted if the object had been declared only for the JVM to call the main() method.
Because the main method in Java does not return anything, its return type is void.
 
What is the meaning of “ import java.util.*;”?
It is a built-in package with a comparable set of classes, sub-packages, and interfaces. The * allows users to import a class from the existing package and use it as many times as they need in the programme
