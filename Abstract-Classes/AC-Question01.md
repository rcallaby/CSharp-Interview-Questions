# Question 1 - Abstract Classes

## What is an abstract class in C#, and how does it differ from an interface?

In C#, both abstract classes and interfaces are used to define contracts that classes must adhere to, but they have some differences in terms of their implementation and usage.

Abstract Class:
An abstract class is a class that cannot be instantiated on its own; it is meant to be subclassed by other classes. Abstract classes can contain a mix of regular (non-abstract) methods and abstract methods. Abstract methods are declared without providing an implementation in the abstract class itself, but any derived class must provide concrete implementations for these abstract methods. Abstract classes can also contain fields, properties, and regular methods with implementations.

Here's an example of an abstract class in C#:

```
abstract class Shape
{
    public abstract double CalculateArea();
    public abstract double CalculatePerimeter();
}

class Circle : Shape
{
    private double radius;

    public Circle(double radius)
    {
        this.radius = radius;
    }

    public override double CalculateArea()
    {
        return Math.PI * radius * radius;
    }

    public override double CalculatePerimeter()
    {
        return 2 * Math.PI * radius;
    }
}

```

In this example, Shape is an abstract class that defines the contract for calculating the area and perimeter of shapes. The Circle class inherits from Shape and provides concrete implementations for the abstract methods.

Interface:
An interface is a contract that specifies a set of methods and properties that implementing classes must provide. Unlike abstract classes, interfaces cannot contain any implementation code; they only define method signatures, properties, events, and indexers. A class can implement multiple interfaces.

Here's an example of an interface in C#:

```
interface IResizable
{
    void Resize(int width, int height);
}

class Rectangle : IResizable
{
    private int width;
    private int height;

    public Rectangle(int width, int height)
    {
        this.width = width;
        this.height = height;
    }

    public void Resize(int newWidth, int newHeight)
    {
        width = newWidth;
        height = newHeight;
    }
}

```
In this example, IResizable is an interface that defines the contract for resizing objects. The Rectangle class implements the interface and provides an implementation for the Resize method.

Key Differences:

Instantiation: Abstract classes cannot be instantiated directly, while interfaces cannot be instantiated at all. Classes that inherit from an abstract class or implement an interface provide the instantiation.

Multiple Inheritance: A class can inherit from only one abstract class (abstract class doesn't support multiple inheritance), but it can implement multiple interfaces.

Method Implementation: Abstract classes can have methods with actual code (both abstract and non-abstract), while interfaces only define method signatures without any implementation.

Fields and Properties: Abstract classes can have fields and properties with implementations, while interfaces cannot have fields and properties with initial values.

Both abstract classes and interfaces serve as ways to define contracts and promote code reusability, but the choice between them depends on the specific design and requirements of your application.
