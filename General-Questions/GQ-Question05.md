# Question 5 - General Questions

## What is an abstract class in C# and when is it used?

In C#, an abstract class is a class that cannot be instantiated directly and must be inherited by a subclass. It is a way to provide a common interface and shared implementation for a group of related classes, while also allowing for individual implementation in each subclass.

An abstract class is defined using the abstract keyword before the class keyword. It can have abstract methods, which are declared without implementation, as well as non-abstract methods with implementation. Subclasses that inherit from the abstract class must implement all abstract methods or else they will also be abstract.

Here is an example of an abstract class in C#:

```csharp
public abstract class Shape
{
    public abstract double GetArea();
    public abstract double GetPerimeter();
}

public class Rectangle : Shape
{
    private double length;
    private double width;
    
    public Rectangle(double length, double width)
    {
        this.length = length;
        this.width = width;
    }
    
    public override double GetArea()
    {
        return length * width;
    }
    
    public override double GetPerimeter()
    {
        return 2 * (length + width);
    }
}

```
In this example, Shape is an abstract class that defines the common interface for shapes, while Rectangle is a concrete subclass that provides its own implementation for the abstract methods. By defining Shape as an abstract class, we can ensure that any subclass of Shape must implement the GetArea and GetPerimeter methods.

Abstract classes are useful when you want to define a common interface and shared implementation for a group of related classes, but you also want to allow for individual implementation in each subclass. They are commonly used in frameworks and APIs to define a base class that provides common functionality for a set of related classes.