# Question 4 - Abstract Classes

## How can abstract classes be used to implement the Factory Method pattern?

The Factory Method pattern is a design pattern that provides an interface for creating objects in a superclass, but allows subclasses to alter the type of objects that will be created. Abstract classes in C# can be used to implement the Factory Method pattern by defining the interface for creating objects in the superclass, but delegating the actual creation of objects to its subclasses.

Here is an example implementation of the Factory Method pattern using abstract classes in C#:

```
// Define the abstract Creator class that provides the interface for creating objects
public abstract class Creator
{
    // The factory method that subclasses must implement to create objects
    public abstract Product FactoryMethod();

    // A method that uses the factory method to create a product
    public void Operation()
    {
        Product product = FactoryMethod();
        Console.WriteLine(product.Operation());
    }
}

// Define the abstract Product class that represents the objects to be created
public abstract class Product
{
    public abstract string Operation();
}

// Define concrete Product classes that implement the Product interface
public class ConcreteProductA : Product
{
    public override string Operation()
    {
        return "ConcreteProductA operation.";
    }
}

public class ConcreteProductB : Product
{
    public override string Operation()
    {
        return "ConcreteProductB operation.";
    }
}

// Define concrete Creator classes that implement the Factory Method to create different types of Products
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

```
In this implementation, the abstract Creator class defines the factory method FactoryMethod() that subclasses must implement to create Product objects. The Creator class also provides a Operation() method that uses the FactoryMethod() to create a Product object and perform an operation on it.

The abstract Product class defines the interface for the objects to be created by the factory method.

The concrete Product classes ConcreteProductA and ConcreteProductB implement the Product interface and define the actual behavior of the objects to be created.

The concrete Creator classes ConcreteCreatorA and ConcreteCreatorB implement the FactoryMethod() to create different types of Product objects. By implementing the FactoryMethod() in each subclass, the type of Product created can be changed without modifying the Creator class.

Here is an example usage of the Factory Method pattern with the above implementation:

```
// Use a ConcreteCreatorA to create a ConcreteProductA
Creator creator = new ConcreteCreatorA();
creator.Operation();  // Output: ConcreteProductA operation.

// Use a ConcreteCreatorB to create a ConcreteProductB
creator = new ConcreteCreatorB();
creator.Operation();  // Output: ConcreteProductB operation.

```
In this usage example, the Creator object is created as either a ConcreteCreatorA or a ConcreteCreatorB, and the Operation() method is called on it to create a Product object and perform an operation on it. The type of Product created depends on the FactoryMethod() implemented in the concrete Creator subclass.
