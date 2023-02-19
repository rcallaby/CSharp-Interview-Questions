# Question 7 - Inheritance

## What is an abstract class in C# and how does it differ from a regular class?

In C#, an abstract class is a class that cannot be instantiated directly and is designed to serve as a base or parent class for other classes. The main difference between an abstract class and a regular class is that an abstract class cannot be used to create objects directly. Instead, it is meant to be subclassed or derived from by other classes.

Here are some key characteristics of abstract classes in C#:

An abstract class may contain both abstract and non-abstract methods and properties.
An abstract method is a method that has no implementation and is marked with the "abstract" keyword. It must be implemented by any non-abstract class that inherits from the abstract class.
An abstract class can also contain non-abstract methods and properties, which can be inherited by non-abstract classes without any modifications.
Any class that inherits from an abstract class must either provide an implementation for all abstract methods in the parent class or be marked as abstract itself.
An abstract class cannot be instantiated directly. Instead, it can only be used as a base class for other classes.
One common use of abstract classes is to define a common interface for a group of related classes. By defining a set of abstract methods and properties, an abstract class can specify the behavior and requirements that all of its subclasses must adhere to. This can help to ensure consistency and maintainability in large codebases.