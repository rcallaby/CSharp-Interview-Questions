# Question 13 - Inheritance

## Can you discuss the differences between virtual methods and abstract methods in C#, and when each should be used?

In C#, both virtual and abstract methods are used for defining methods that can be overridden by derived classes. However, there are some differences between the two.

+ Virtual Methods:
A virtual method is a method that can be overridden in a derived class. It provides a default implementation of a method that can be replaced with a derived class-specific implementation. The virtual keyword is used to define a virtual method.

Example:

```csharp
public class MyBaseClass
{
   public virtual void MyVirtualMethod()
   {
      Console.WriteLine("This is the base class virtual method.");
   }
}

public class MyDerivedClass : MyBaseClass
{
   public override void MyVirtualMethod()
   {
      Console.WriteLine("This is the derived class override of the virtual method.");
   }
}

```
+ Abstract Methods:
An abstract method is a method that does not have a default implementation in the base class and must be implemented by any derived class. Abstract methods are defined using the abstract keyword and must be implemented by the derived classes. Abstract methods are used to define a common interface or contract that derived classes must implement.

Example:

```csharp
public abstract class MyBaseClass
{
   public abstract void MyAbstractMethod();
}

public class MyDerivedClass : MyBaseClass
{
   public override void MyAbstractMethod()
   {
      Console.WriteLine("This is the derived class implementation of the abstract method.");
   }
}

```
+ When to use virtual methods:
Virtual methods are useful when you want to provide a default implementation of a method that can be overridden by a derived class. Virtual methods are often used in base classes to provide a default behavior that can be customized in the derived classes.

+ When to use abstract methods:
Abstract methods are useful when you want to define a common interface or contract that derived classes must implement. Abstract methods are often used in abstract classes and interfaces to define the behavior that must be implemented by the derived classes. Abstract methods are also useful when you want to ensure that the derived classes implement a specific behavior or functionality.