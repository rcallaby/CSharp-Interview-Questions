# Question 3 - Inheritance

## What is the difference between single inheritance and multiple inheritance in C#?

In C#, single inheritance and multiple inheritance refer to the ways in which a derived class can inherit properties and methods from its parent class or classes.

Single inheritance is when a derived class inherits from a single base class. This means that the derived class can only inherit the properties and methods of one parent class. In C#, a class can only inherit from a single base class using the "class : baseclass" syntax.

Multiple inheritance, on the other hand, is when a derived class inherits from multiple base classes. This means that the derived class can inherit properties and methods from more than one parent class. In C#, multiple inheritance is not directly supported. However, it can be achieved using interfaces. An interface is a contract that specifies a set of properties and methods that a class must implement. A class can implement multiple interfaces, effectively inheriting properties and methods from multiple sources.

The key difference between single inheritance and multiple inheritance is that single inheritance provides a simpler and more streamlined class hierarchy, whereas multiple inheritance provides greater flexibility and code reuse by allowing a class to inherit from multiple sources. However, multiple inheritance can also be more complex and potentially lead to conflicts between the inherited properties and methods from the different sources.