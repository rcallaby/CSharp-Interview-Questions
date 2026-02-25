# Question 9 - Design Patterns

## What is the Prototype pattern in C# and how does it differ from the Factory Method pattern?

The Prototype pattern and the Factory Method pattern are both creational design patterns in object-oriented programming, but they serve different purposes and have distinct implementations. Let's dive into each pattern with examples in C# to understand the differences.

Prototype Pattern:
The Prototype pattern involves creating new objects by copying an existing object, known as the prototype. It's useful when creating new objects is costly in terms of time and resources, and you want to create new instances by cloning an existing one. This pattern is particularly effective when you have a complex object that's expensive to initialize, and you want to create variations of it quickly.

```
using System;

// Prototype base class
abstract class ShapePrototype
{
    public abstract ShapePrototype Clone();
}

// Concrete prototype
class Circle : ShapePrototype
{
    public int Radius { get; set; }

    public override ShapePrototype Clone()
    {
        return (Circle)MemberwiseClone();
    }
}

class Program
{
    static void Main(string[] args)
    {
        Circle originalCircle = new Circle { Radius = 5 };
        Circle clonedCircle = (Circle)originalCircle.Clone();

        Console.WriteLine($"Original Circle Radius: {originalCircle.Radius}");
        Console.WriteLine($"Cloned Circle Radius: {clonedCircle.Radius}");

        Console.WriteLine($"Are the circles the same object? {(originalCircle == clonedCircle)}");
    }
}

```

In the above example, the Circle class serves as a prototype, and the Clone method creates a shallow copy of the object using MemberwiseClone. The Prototype pattern allows you to create new instances by cloning an existing one, avoiding expensive object creation.

Factory Method Pattern:
The Factory Method pattern focuses on creating objects through a dedicated factory method. This method is typically defined in an interface or an abstract class and implemented by concrete classes to create instances of related objects. It allows you to encapsulate the object creation process and delegate the responsibility to subclasses.

```
using System;

// Product interface
interface IProduct
{
    void Display();
}

// Concrete products
class ConcreteProductA : IProduct
{
    public void Display()
    {
        Console.WriteLine("Concrete Product A");
    }
}

class ConcreteProductB : IProduct
{
    public void Display()
    {
        Console.WriteLine("Concrete Product B");
    }
}

// Creator abstract class
abstract class Creator
{
    public abstract IProduct FactoryMethod();
}

// Concrete creators
class ConcreteCreatorA : Creator
{
    public override IProduct FactoryMethod()
    {
        return new ConcreteProductA();
    }
}

class ConcreteCreatorB : Creator
{
    public override IProduct FactoryMethod()
    {
        return new ConcreteProductB();
    }
}

class Program
{
    static void Main(string[] args)
    {
        Creator creatorA = new ConcreteCreatorA();
        IProduct productA = creatorA.FactoryMethod();
        productA.Display();

        Creator creatorB = new ConcreteCreatorB();
        IProduct productB = creatorB.FactoryMethod();
        productB.Display();
    }
}

```
In this example, the Factory Method pattern is used to create instances of products (ConcreteProductA and ConcreteProductB) through their respective creators (ConcreteCreatorA and ConcreteCreatorB). The key difference from the Prototype pattern is that the Factory Method pattern focuses on creating objects using dedicated factory methods, while the Prototype pattern emphasizes cloning existing objects.

In summary, the Prototype pattern involves cloning existing objects to create new ones, whereas the Factory Method pattern uses factory methods to create instances of related objects.
