# Question 7 - LINQ

##  Can you demonstrate the use of LINQ to implement the Open-Closed Principle (OCP)?

The Open-Closed Principle is a SOLID design principle that states that software entities (classes, modules, functions, etc.) should be open for extension but closed for modification. This means that you should be able to extend the behavior of a software entity without modifying its existing code.

LINQ (Language Integrated Query) is a powerful feature of .NET that allows you to query collections of objects in a declarative way. You can use LINQ to implement the OCP by creating abstractions that allow you to extend the behavior of a collection without modifying its existing code. Here's an example:

Let's say we have a collection of shapes:

```
public abstract class Shape
{
    public abstract double Area { get; }
}

public class Circle : Shape
{
    public double Radius { get; set; }
    public override double Area => Math.PI * Radius * Radius;
}

public class Rectangle : Shape
{
    public double Width { get; set; }
    public double Height { get; set; }
    public override double Area => Width * Height;
}

public class Triangle : Shape
{
    public double Base { get; set; }
    public double Height { get; set; }
    public override double Area => 0.5 * Base * Height;
}

List<Shape> shapes = new List<Shape>
{
    new Circle { Radius = 3 },
    new Rectangle { Width = 4, Height = 5 },
    new Triangle { Base = 3, Height = 4 },
    new Circle { Radius = 5 },
    new Rectangle { Width = 2, Height = 3 }
};

```
Now, let's say we want to calculate the total area of all the shapes in the collection. We can do this using LINQ:

```
double totalArea = shapes.Sum(s => s.Area);

```
This code uses the Sum method of LINQ to calculate the sum of the areas of all the shapes in the collection. The Sum method takes a lambda expression that specifies the function to apply to each element of the collection.

Now, let's say we want to add a new type of shape to our collection, such as a Square. We can do this without modifying the existing code by creating a new class that derives from Shape and implementing the Area property:

```
public class Square : Shape
{
    public double Side { get; set; }
    public override double Area => Side * Side;
}

```
We can now add a Square object to our collection and calculate the total area without modifying the existing LINQ code:

```
shapes.Add(new Square { Side = 2 });
double newTotalArea = shapes.Sum(s => s.Area);

```
This demonstrates the Open-Closed Principle in action. We were able to extend the behavior of the collection by adding a new type of shape without modifying the existing code that calculates the total area using LINQ.