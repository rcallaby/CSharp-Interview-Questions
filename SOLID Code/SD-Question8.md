# Question 8 - SOLID

## Can you explain the Liskov Substitution Principle in your own words, and provide an example of how it can be violated in C# code?

The Liskov Substitution Principle (LSP) is a fundamental principle of object-oriented programming that states that any instance of a derived class should be able to be used in place of an instance of its parent class without affecting the correctness of the program.

In other words, if a program is written to work with a certain base class, any derived classes should be able to be used interchangeably with the base class without breaking the program. This allows for greater flexibility in the design of object-oriented programs and can make them more modular and easier to maintain.

For example, let's say we have a base class called Shape and two derived classes called Rectangle and Circle. Shape has a method called CalculateArea() that calculates the area of the shape. If we follow the LSP, we should be able to substitute a Rectangle or a Circle for a Shape and still be able to call the CalculateArea() method without any issues.

Here's an example of how the LSP can be violated in C# code:

```
public class Rectangle
{
    public int Width { get; set; }
    public int Height { get; set; }

    public int CalculateArea()
    {
        return Width * Height;
    }
}

public class Square : Rectangle
{
    public new int Width
    {
        get { return base.Width; }
        set { base.Width = base.Height = value; }
    }

    public new int Height
    {
        get { return base.Height; }
        set { base.Height = base.Width = value; }
    }
}

```
In this example, we have a Rectangle class with a CalculateArea() method that returns the area of the rectangle. We also have a Square class that inherits from Rectangle. However, the Square class overrides the Width and Height properties of Rectangle to always be the same value (since a square has equal width and height).

The problem with this implementation is that a Square instance cannot be used interchangeably with a Rectangle instance. For example, if we have a method that takes a Rectangle parameter and expects it to have a certain width and height, it will not work correctly if we pass in a Square instead, because the Square will always have equal width and height.

This violates the LSP, as a Square is not a true substitute for a Rectangle in all cases.