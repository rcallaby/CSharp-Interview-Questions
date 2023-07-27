# Question 13 - Abstract Class

## Is it possible in C# that a class inherit from multiple abstract classes?

No, in C#, a class cannot directly inherit from multiple abstract classes. C# supports single inheritance for classes, which means a class can only inherit from one base class. This is a fundamental design choice in the language.

However, C# allows a class to implement multiple interfaces. Interfaces are similar to abstract classes in that they define a contract for the derived classes, but they cannot provide any implementation details. A class can implement multiple interfaces, effectively providing a form of multiple inheritance through interfaces.

Here's an example to illustrate this:

```
// Abstract class 1
public abstract class Shape
{
    public abstract double Area();
}

// Abstract class 2
public abstract class Colorful
{
    public abstract string GetColor();
}

// Concrete class implementing multiple interfaces
public class Circle : Shape, Colorful
{
    private double radius;
    private string color;

    public Circle(double radius, string color)
    {
        this.radius = radius;
        this.color = color;
    }

    public override double Area()
    {
        return Math.PI * radius * radius;
    }

    public string GetColor()
    {
        return color;
    }
}

```
In this example, the class Circle inherits from the Shape abstract class and implements the Colorful interface. This allows Circle to provide its own implementation for the Area() method and the GetColor() method.

If you need a class to have behavior from multiple sources resembling abstract classes, you can use a combination of abstract classes and interfaces to achieve that. Create one abstract class that holds the common behavior and then have the class implement interfaces to handle other aspects.
