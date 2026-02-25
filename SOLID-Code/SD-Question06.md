# Question 6 - SOLID

## Can you explain the Open-Closed Principle in C#, and provide an example of how it can be implemented in code?

The Open-Closed Principle (OCP) is a design principle in object-oriented programming (OOP) that states that software entities (classes, modules, functions, etc.) should be open for extension but closed for modification. In other words, you should be able to add new features to a system without changing the existing code.

In C#, the Open-Closed Principle can be implemented using interfaces, abstract classes, and inheritance. The idea is to create an abstraction that defines the behavior of a system, and then use this abstraction to implement specific functionality.

Here is an example of how the Open-Closed Principle can be implemented in C#:

```
// Define an interface for a shape
public interface IShape
{
    double GetArea();
}

// Define a rectangle class that implements the IShape interface
public class Rectangle : IShape
{
    public double Width { get; set; }
    public double Height { get; set; }

    public double GetArea()
    {
        return Width * Height;
    }
}

// Define a circle class that implements the IShape interface
public class Circle : IShape
{
    public double Radius { get; set; }

    public double GetArea()
    {
        return Math.PI * Math.Pow(Radius, 2);
    }
}

// Define a client class that uses the IShape interface
public class Client
{
    public void PrintArea(IShape shape)
    {
        Console.WriteLine("The area of the shape is: " + shape.GetArea());
    }
}

// Use the client class to print the areas of different shapes
static void Main(string[] args)
{
    Client client = new Client();

    Rectangle rectangle = new Rectangle { Width = 10, Height = 5 };
    Circle circle = new Circle { Radius = 3 };

    client.PrintArea(rectangle);
    client.PrintArea(circle);
}

```
In this example, we define an interface called IShape that defines the behavior of a shape. We then create two classes, Rectangle and Circle, that implement the IShape interface. Finally, we create a client class called Client that takes an IShape object as a parameter and prints its area.

By using an interface to define the behavior of a shape, we make our system open for extension. We can add new shapes to the system by implementing the IShape interface without changing the existing code. At the same time, we make our system closed for modification, since we don't need to change the Client class to add new shapes.