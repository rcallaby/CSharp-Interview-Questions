# Question 1 - Abstract Classes

## What is an abstract class in C#, and how does it differ from an interface?

In C#, an abstract class is a class that cannot be instantiated and serves as a base class for other classes to derive from. It can contain both abstract and non-abstract members, methods, and properties. An abstract member does not have a definition and must be implemented by the derived class.

On the other hand, an interface is a contract that defines a set of properties, methods, and events that a class must implement. It only contains abstract members and does not provide any implementation. A class can implement multiple interfaces, but it can only inherit from one base class.

The main differences between an abstract class and an interface are:

Instantiation: An abstract class cannot be instantiated directly, while an interface cannot be instantiated at all.

Implementation: An abstract class can contain both abstract and non-abstract members, while an interface only contains abstract members that must be implemented by the class that implements it.

Inheritance: A class can inherit from only one abstract class, but can implement multiple interfaces.

Access modifiers: Members of an interface are public by default, while members of an abstract class can have any access modifier.

In summary, an abstract class is used when you want to provide a base implementation for the derived class, while an interface is used when you want to enforce a contract on the class that implements it.