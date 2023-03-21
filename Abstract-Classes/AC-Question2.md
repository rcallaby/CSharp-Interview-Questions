# Question 2 - Abstract Classes

## How can abstract classes be used to implement the Template Method design pattern?

The Template Method design pattern is a behavioral pattern that defines the skeleton of an algorithm in a superclass, but lets subclasses override specific steps of the algorithm without changing its structure. This pattern can be implemented using abstract classes in C#.

Here is an example of how abstract classes can be used to implement the Template Method design pattern:

```
public abstract class AbstractClass
{
    // The template method defines the skeleton of the algorithm.
    public void TemplateMethod()
    {
        Operation1();
        Operation2();
    }

    // These abstract methods will be implemented by the subclasses.
    protected abstract void Operation1();
    protected abstract void Operation2();
}

public class ConcreteClassA : AbstractClass
{
    protected override void Operation1()
    {
        Console.WriteLine("ConcreteClassA.Operation1");
    }

    protected override void Operation2()
    {
        Console.WriteLine("ConcreteClassA.Operation2");
    }
}

public class ConcreteClassB : AbstractClass
{
    protected override void Operation1()
    {
        Console.WriteLine("ConcreteClassB.Operation1");
    }

    protected override void Operation2()
    {
        Console.WriteLine("ConcreteClassB.Operation2");
    }
}

```
In this example, AbstractClass is the abstract class that defines the template method TemplateMethod(). This method calls two abstract methods Operation1() and Operation2(). These methods will be implemented by the subclasses ConcreteClassA and ConcreteClassB.

When a client wants to use the algorithm, it creates an instance of one of the concrete classes and calls the template method:

```
AbstractClass abstractClass = new ConcreteClassA();
abstractClass.TemplateMethod();

```
This will output:

```
ConcreteClassA.Operation1
ConcreteClassA.Operation2

```
Similarly, the client can create an instance of ConcreteClassB and call the template method:

```
AbstractClass abstractClass = new ConcreteClassB();
abstractClass.TemplateMethod();

```
This will output:

```
ConcreteClassB.Operation1
ConcreteClassB.Operation2

```
In this way, the Template Method design pattern can be implemented using abstract classes in C#.
