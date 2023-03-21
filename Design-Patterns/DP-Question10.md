# Question 10 - Design Patterns

## How can you use the Facade pattern in C# to simplify a complex system?

The Facade pattern is a design pattern used to provide a simplified interface to a complex system. It defines a higher-level interface that makes the underlying system easier to use by encapsulating the complexities of the system and providing a simple, user-friendly interface. In C#, you can implement the Facade pattern by creating a class that acts as a facade, or a front-end, for the complex system. This class provides a simplified, unified interface to the complex system and acts as a proxy for the underlying components.

Here's a simple example of how you might implement the Facade pattern in C#:

```
public class ComplexSystem
{
    public void MethodA()
    {
        Console.WriteLine("ComplexSystem MethodA");
    }

    public void MethodB()
    {
        Console.WriteLine("ComplexSystem MethodB");
    }
}

public class Facade
{
    private ComplexSystem _complexSystem;

    public Facade(ComplexSystem complexSystem)
    {
        _complexSystem = complexSystem;
    }

    public void Method1()
    {
        Console.WriteLine("Facade Method1");
        _complexSystem.MethodA();
    }

    public void Method2()
    {
        Console.WriteLine("Facade Method2");
        _complexSystem.MethodB();
    }
}

class Program
{
    static void Main(string[] args)
    {
        ComplexSystem complexSystem = new ComplexSystem();
        Facade facade = new Facade(complexSystem);

        facade.Method1();
        facade.Method2();

        Console.ReadKey();
    }
}

```
In this example, the ComplexSystem class represents the complex system that we want to simplify. The Facade class provides a simplified interface to the ComplexSystem class by encapsulating its complexity and providing a unified interface. The Facade class's methods Method1 and Method2 provide a simple, unified way to access the underlying functionality of the ComplexSystem class. This makes it easier to use the complex system, as the client code can interact with the system through the Facade class instead of directly with the complex system.
