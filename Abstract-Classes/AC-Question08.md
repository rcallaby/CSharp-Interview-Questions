# Question 8 - Abstract Classes

## What is the difference between an abstract class and a concrete class in C#, and how does this relate to the Open-Closed principle?

In C#, an abstract class is a class that cannot be instantiated directly, but instead serves as a template for other classes to inherit from. It is typically used to define a set of common characteristics or behaviors that all derived classes should have. Abstract classes may contain one or more abstract methods, which are declared without an implementation and must be implemented by any derived class.

On the other hand, a concrete class is a class that can be instantiated directly and provides an implementation for all its methods. It does not contain any abstract methods and can be used as-is without any need for further implementation.

The Open-Closed principle is a principle in object-oriented programming that states that classes should be open for extension but closed for modification. This means that a class should be designed in such a way that it can be easily extended to add new functionality without modifying its existing code.

Abstract classes and interfaces are typically used to achieve this principle. By defining an abstract class that contains a set of abstract methods, the class can be easily extended by creating new derived classes that implement these abstract methods. This allows for new functionality to be added to the system without modifying the existing code. In contrast, concrete classes that do not use abstract methods may be more difficult to extend without modifying the existing code.

In summary, the difference between an abstract class and a concrete class in C# is that an abstract class provides a template for other classes to inherit from and contains one or more abstract methods that must be implemented by any derived class, while a concrete class can be instantiated directly and provides an implementation for all its methods. The use of abstract classes and interfaces can help to achieve the Open-Closed principle by allowing for easy extension of a system without modifying its existing code.