# Question 3 - Design Patterns

## What is the factory method and how is it used?

The factory method is a creational design pattern that provides an interface for creating objects in a superclass, but allows subclasses to alter the type of objects that will be created. In C#, the factory method can be implemented by defining a factory method in a base class that returns an object of the type of the base class, but the concrete implementation of the method is provided by subclasses.

Below is a bit of sample code:

```
public abstract class Creator
{
    public abstract Product FactoryMethod();
}

public class ConcreteCreatorA : Creator
{
    public override Product FactoryMethod()
    {
        return new ConcreteProductA();
    }
}

public class ConcreteCreatorB : Creator
{
    public override Product FactoryMethod()
    {
        return new ConcreteProductB();
    }
}

public abstract class Product
{
}

public class ConcreteProductA : Product
{
}

public class ConcreteProductB : Product
{
}

```
In this example, the abstract Creator class defines the FactoryMethod method which is implemented by the ConcreteCreatorA and ConcreteCreatorB classes. 

The ConcreteCreatorA class returns an instance of ConcreteProductA, while the ConcreteCreatorB class returns an instance of ConcreteProductB. The factory method pattern allows the client code to be decoupled from the concrete classes, and the choice of which product to create is made at runtime based on the concrete creator class being used.
