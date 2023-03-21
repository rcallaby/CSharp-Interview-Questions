# Question 20 - Design Patterns

## Can you explain the use of the Visitor pattern in C# for adding new operations to existing objects without modifying their source code?

The Visitor pattern is a design pattern in software engineering that allows you to add new operations to existing objects without modifying their source code. The idea behind this pattern is to separate the actual operations on objects from the objects themselves.

Here's how it works:

You define a visitor interface that specifies the operations that can be performed on the objects.

```
public interface IVisitor
{
    void Visit(ElementA elementA);
    void Visit(ElementB elementB);
}
```
You then create concrete implementations of the visitor interface for each new operation that you want to perform.

```
public class ConcreteVisitor1 : IVisitor
{
    public void Visit(ElementA elementA)
    {
        Console.WriteLine("Visiting ElementA using ConcreteVisitor1");
    }

    public void Visit(ElementB elementB)
    {
        Console.WriteLine("Visiting ElementB using ConcreteVisitor1");
    }
}

public class ConcreteVisitor2 : IVisitor
{
    public void Visit(ElementA elementA)
    {
        Console.WriteLine("Visiting ElementA using ConcreteVisitor2");
    }

    public void Visit(ElementB elementB)
    {
        Console.WriteLine("Visiting ElementB using ConcreteVisitor2");
    }
}

```
You then add an Accept method to each element that you want to perform operations on. The Accept method takes an IVisitor as an argument and calls the appropriate Visit method.

```
public abstract class Element
{
    public abstract void Accept(IVisitor visitor);
}

public class ElementA : Element
{
    public override void Accept(IVisitor visitor)
    {
        visitor.Visit(this);
    }
}

public class ElementB : Element
{
    public override void Accept(IVisitor visitor)
    {
        visitor.Visit(this);
    }
}

```
To perform an operation on an object, you create an instance of the appropriate concrete visitor and call the Accept method on the object.

```
ElementA elementA = new ElementA();
ElementB elementB = new ElementB();

ConcreteVisitor1 concreteVisitor1 = new ConcreteVisitor1();
ConcreteVisitor2 concreteVisitor2 = new ConcreteVisitor2();

elementA.Accept(concreteVisitor1);
elementB.Accept(concreteVisitor1);

elementA.Accept(concreteVisitor2);
elementB.Accept(concreteVisitor2);

```
This pattern allows you to add new operations to existing objects without modifying their source code, as the operations are defined in separate classes. It also provides a clean way to manage multiple operations on objects, as each operation is defined in its own concrete visitor class.