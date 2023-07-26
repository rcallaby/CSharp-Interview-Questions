# Question 12 - Abstract Class

## Is it possible for an abstract class to contain a main method in C#?


In C#, it is possible for an abstract class to contain a static main method. However, you won't be able to create an instance of an abstract class directly because abstract classes are meant to be subclassed and used as base classes. The main method is the entry point of a C# application and is usually found in a static class. When it comes to abstract classes, you can use them in combination with concrete classes that derive from them.

Let's see an example:

```
using System;

// Abstract class with a static main method
abstract class Shape
{
    public abstract void Draw();

    public static void Main(string[] args)
    {
        // Since the class is abstract, we can't create an instance of it.
        // Let's create instances of its subclasses to demonstrate.
        Shape shape1 = new Circle();
        Shape shape2 = new Square();

        shape1.Draw();
        shape2.Draw();
    }
}

// Concrete subclass 1
class Circle : Shape
{
    public override void Draw()
    {
        Console.WriteLine("Drawing a circle.");
    }
}

// Concrete subclass 2
class Square : Shape
{
    public override void Draw()
    {
        Console.WriteLine("Drawing a square.");
    }
}

```

In this example, we have an abstract class Shape with an abstract method Draw(). The class also contains a static Main method. Notice that you can't directly create an instance of the Shape class, but you can create instances of its subclasses, Circle and Square.

When you run this program, the Main method will be the entry point and will execute the Draw method for both the Circle and Square instances, as they are assigned to variables of the abstract class Shape.

Remember, the Main method can only be declared in a static class, but an abstract class can contain static members like the Main method.