# Question 3 - General Questions

## What is inheritance in C# and how does it work?

Inheritance in C# is a mechanism by which a new class can be derived from an existing class, known as the base class or superclass. The derived class, known as the subclass or child class, inherits all the properties, methods, and fields of the base class and can also add new properties, methods, and fields of its own.

To create a derived class in C#, you use the colon (:) symbol after the name of the derived class and specify the name of the base class. For example:

```csharp
class ChildClass : BaseClass
{
    // Add new properties, methods, and fields here
}

```
Once you have defined the child class, you can create objects of that class that will inherit all the properties, methods, and fields of the base class, as well as any additional ones defined in the child class.

Inheritance allows you to create a hierarchy of related classes, where each class inherits from the one above it. This can help you to write more modular, reusable code, as you can define common behavior in the base class and then add specific behavior in the child classes.

C# also supports multiple inheritance, where a class can inherit from more than one base class, but this is achieved through the use of interfaces rather than direct inheritance.