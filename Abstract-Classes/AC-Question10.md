# Question 10 - Abstract Classes

## How can abstract classes be used to implement the Strategy design pattern?

The Strategy design pattern is a behavioral design pattern that allows you to define a family of algorithms, encapsulate each one as an object, and make them interchangeable at runtime. Abstract classes in C# can be used to implement the Strategy design pattern by defining a common interface for all the algorithms in the family and providing a set of concrete implementations that can be swapped out at runtime.

Here's an example of how to use abstract classes to implement the Strategy design pattern in C#:

Define an abstract base class that provides the common interface for all the algorithms in the family. This abstract base class should define an abstract method that represents the algorithm.

```
public abstract class Strategy
{
    public abstract void Algorithm();
}

```
Define concrete subclasses that implement the abstract method defined in the abstract base class. Each concrete subclass represents a specific algorithm in the family.

```
public class ConcreteStrategyA : Strategy
{
    public override void Algorithm()
    {
        // implement algorithm A
    }
}

public class ConcreteStrategyB : Strategy
{
    public override void Algorithm()
    {
        // implement algorithm B
    }
}

```
Define a context class that uses the Strategy objects. The context class should have a property that holds a reference to a Strategy object and a method that invokes the algorithm defined in the Strategy object.

```
public class Context
{
    private Strategy _strategy;

    public void SetStrategy(Strategy strategy)
    {
        _strategy = strategy;
    }

    public void ExecuteAlgorithm()
    {
        _strategy.Algorithm();
    }
}

```
Use the context class to execute different algorithms at runtime by setting the appropriate Strategy object using the SetStrategy method and then invoking the ExecuteAlgorithm method.

```
Context context = new Context();

context.SetStrategy(new ConcreteStrategyA());
context.ExecuteAlgorithm(); // executes algorithm A

context.SetStrategy(new ConcreteStrategyB());
context.ExecuteAlgorithm(); // executes algorithm B

```
In this example, the abstract base class Strategy defines the common interface for all the algorithms in the family, while the concrete subclasses ConcreteStrategyA and ConcreteStrategyB provide specific implementations of the algorithms. The context class Context uses the Strategy objects to execute the algorithms at runtime, and the client code can switch between different algorithms by setting the appropriate Strategy object using the SetStrategy method.
