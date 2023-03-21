# Question 2 - Clean Code

## Can you explain the SOLID principles of object-oriented programming and how they can be applied to C# code?

SOLID is an acronym that stands for five principles of object-oriented programming, aimed at creating maintainable and scalable software systems. These principles are:

Single Responsibility Principle (SRP): A class should have only one reason to change, meaning that it should have only one responsibility.

Open/Closed Principle (OCP): Software entities (classes, modules, functions, etc.) should be open for extension but closed for modification, meaning that you should be able to add new features to a class without changing its existing code.

Liskov Substitution Principle (LSP): Subtypes must be substitutable for their base types, meaning that if a class is a subtype of another class, it should be able to be used wherever the base class can be used without affecting the correctness of the program.

Interface Segregation Principle (ISP): Clients should not be forced to depend on interfaces they do not use, meaning that you should split large interfaces into smaller, more specialized ones.

Dependency Inversion Principle (DIP): High-level modules should not depend on low-level modules; both should depend on abstractions, meaning that you should depend on abstractions, not on concrete implementations.

Here is an example of how these principles can be applied to C# code:

SRP: To apply SRP in C#, you can extract responsibilities into separate classes, so each class has only one reason to change. For example, consider a class that performs both input validation and database access. You can extract the validation logic into a separate class and have the original class depend on it.

OCP: To apply OCP in C#, you can use polymorphism, abstract classes, and interfaces to allow for extensions without changing existing code. For example, consider a class that performs some operation. You can extract an interface that defines the operation, and allow clients to provide their own implementation of the operation, without changing the existing code.

LSP: To apply LSP in C#, you can ensure that subclasses override base class methods in a way that is compatible with the base class contract. For example, consider a base class with a method that performs some calculation. You can extract an interface that defines the calculation, and have the base class implement it. Subclasses can then override the method and provide their own implementation of the calculation, as long as it is compatible with the base class contract.

ISP: To apply ISP in C#, you can extract smaller, more specialized interfaces from larger ones. For example, consider a large interface that defines many methods. You can extract smaller interfaces, each defining a subset of the methods, and have the original interface depend on them. Clients can then choose to implement only the interfaces they need, without being forced to implement methods they do not use.

DIP: To apply DIP in C#, you can use dependency injection to control the dependencies of a class. For example, consider a class that depends on a database. You can extract an interface that defines the database operations, and have the class depend on it. You can then provide a concrete implementation of the interface, without changing the existing code.

By following these SOLID principles, you can create maintainable and scalable C# code that is easy to extend and modify.