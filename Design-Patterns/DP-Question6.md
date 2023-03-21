# Question 6 - Design Patterns

## How can you use the Decorator Pattern in C# to extend the behavior of an object dynamically?

The Decorator pattern is a structural design pattern that allows you to add behavior to an object dynamically by wrapping it in another object that provides the desired behavior. The decorator object acts as a wrapper around the original object, and implements the same interface as the original object. This allows the decorator object to be used in the same way as the original object, while adding the desired behavior.

Here's an example of how you can use the Decorator pattern in C# to extend the behavior of an object dynamically:

```
using System;

// The interface that defines the objects we want to decorate
interface IComponent
{
    void Operation();
}

// The concrete component that we want to decorate
class ConcreteComponent : IComponent
{
    public void Operation()
    {
        Console.WriteLine("ConcreteComponent.Operation()");
    }
}

// The abstract decorator class that implements the IComponent interface
abstract class Decorator : IComponent
{
    protected IComponent component;

    public Decorator(IComponent component)
    {
        this.component = component;
    }

    public virtual void Operation()
    {
        component.Operation();
    }
}

// A concrete decorator that adds behavior to the component
class ConcreteDecoratorA : Decorator
{
    public ConcreteDecoratorA(IComponent component) : base(component)
    {
    }

    public override void Operation()
    {
        base.Operation();
        Console.WriteLine("ConcreteDecoratorA.Operation()");
    }
}

// Another concrete decorator that adds behavior to the component
class ConcreteDecoratorB : Decorator
{
    public ConcreteDecoratorB(IComponent component) : base(component)
    {
    }

    public override void Operation()
    {
        base.Operation();
        Console.WriteLine("ConcreteDecoratorB.Operation()");
    }
}

class Program
{
    static void Main(string[] args)
    {
        // Create a concrete component
        IComponent component = new ConcreteComponent();

        // Decorate the component with ConcreteDecoratorA
        IComponent decoratedComponent = new ConcreteDecoratorA(component);

        // Decorate the decorated component with ConcreteDecoratorB
        decoratedComponent = new ConcreteDecoratorB(decoratedComponent);

        // Invoke the operation on the decorated component
        decoratedComponent.Operation();

        Console.ReadLine();
    }
}

```
In this example, we first create a concrete component ConcreteComponent that implements the IComponent interface. Then, we create two concrete decorator classes ConcreteDecoratorA and ConcreteDecoratorB that add behavior to the component by wrapping it in an object that provides the desired behavior. The decorators extend the Decorator abstract class, which implements the IComponent interface and delegates the operation to the decorated component.

Finally, in the main method, we create a concrete component, and decorate it with ConcreteDecoratorA and ConcreteDecoratorB in turn. When we invoke the operation on the decorated component, it first performs the operation of ConcreteComponent, then performs the operation of ConcreteDecoratorA, and finally performs
