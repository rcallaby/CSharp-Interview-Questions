# Question 7 - Generic Types

## How can you create a generic interface in C#?

In C#, you can create a generic interface by using the "interface" keyword followed by the interface name, and then specifying one or more type parameters within angle brackets "<>".

Here is an example of a generic interface with a single type parameter:

```csharp
public interface IMyInterface<T>
{
    void DoSomething(T item);
}

```
In this example, the interface "IMyInterface" has one type parameter "T". The method "DoSomething" takes an argument of type "T".

To use this interface, you would specify a concrete type for the type parameter when you implement the interface. For example, if you want to implement the interface for a list of integers, you would define a class that implements the interface like this:

```csharp
public class MyList : IMyInterface<int>
{
    public void DoSomething(int item)
    {
        // implementation here
    }
}

```
In this example, the "MyList" class implements the "IMyInterface" interface for type "int", and provides an implementation for the "DoSomething" method.

By using a generic interface, you can write reusable code that can work with different types, without having to write separate interfaces for each type.