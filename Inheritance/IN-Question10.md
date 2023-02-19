# Question 10 - Inheritance

## How can you use inheritance and polymorphism together to achieve dynamic dispatch in C#?

In C#, inheritance and polymorphism can be used together to achieve dynamic dispatch through method overriding. Dynamic dispatch allows for the selection of the most appropriate method to be called based on the runtime type of the object.

To achieve dynamic dispatch in C# using inheritance and polymorphism, you can follow these steps:

Define a base class with a virtual method. This base class will serve as the superclass for all derived classes. The virtual method can be overridden by the derived classes.

```
public class Shape
{
    public virtual void Draw()
    {
        Console.WriteLine("Drawing a shape.");
    }
}

```
Define a derived class that inherits from the base class and overrides the virtual method. The derived class can implement its own version of the method.

```
public class Circle : Shape
{
    public override void Draw()
    {
        Console.WriteLine("Drawing a circle.");
    }
}

```
Instantiate an object of the derived class and call the virtual method. The runtime type of the object will determine which version of the method will be called.

```
Shape shape1 = new Shape();
Shape shape2 = new Circle();

shape1.Draw(); // Output: "Drawing a shape."
shape2.Draw(); // Output: "Drawing a circle."

```
In the above code, shape1 is an instance of the Shape class, so calling Draw() will invoke the method in the Shape class. However, shape2 is an instance of the Circle class, so calling Draw() will invoke the overridden method in the Circle class.

This is an example of dynamic dispatch using inheritance and polymorphism in C#. The appropriate method is selected at runtime based on the actual type of the object, allowing for flexible and extensible code.
