# Question 16 - Design Patterns

## Can you explain the use of the Bridge pattern in C# to separate the abstraction from its implementation?

The Bridge pattern is a structural design pattern that separates an object's interface from its implementation. It allows the two to evolve independently, which is especially useful when a change to one part of an object-oriented design would otherwise force changes to the other part.

The Bridge pattern consists of two parts: the Abstraction and the Implementation. The Abstraction is an interface or an abstract class that defines the high-level, or abstract, interface to the client. The Implementation is a concrete class that implements the Abstraction's interface.

In C#, you can use the Bridge pattern by defining two separate class hierarchies: one for the Abstraction, and one for the Implementation. The Abstraction defines the interface that the client will use, while the Implementation defines the concrete implementation of the Abstraction's interface.

Here's an example that demonstrates the Bridge pattern in C#:

```
// Abstraction hierarchy
public abstract class Shape
{
    protected IColor color;

    protected Shape(IColor color)
    {
        this.color = color;
    }

    public abstract void Draw();
}

public class Circle : Shape
{
    public Circle(IColor color) : base(color)
    { }

    public override void Draw()
    {
        Console.WriteLine("Drawing Circle with color " + color.Fill());
    }
}

public class Square : Shape
{
    public Square(IColor color) : base(color)
    { }

    public override void Draw()
    {
        Console.WriteLine("Drawing Square with color " + color.Fill());
    }
}

// Implementation hierarchy
public interface IColor
{
    string Fill();
}

public class Red : IColor
{
    public string Fill()
    {
        return "Red";
    }
}

public class Green : IColor
{
    public string Fill()
    {
        return "Green";
    }
}

```
In this example, the Shape class hierarchy defines the Abstraction, while the IColor hierarchy defines the Implementation. The Shape class takes a IColor object as an argument in its constructor and uses it to fill the color of the shape. This allows you to change the color of the shape without changing the implementation of the Shape class. The client code can use the Shape and IColor classes as follows:

```
Shape circle = new Circle(new Red());
circle.Draw();

Shape square = new Square(new Green());
square.Draw();
```