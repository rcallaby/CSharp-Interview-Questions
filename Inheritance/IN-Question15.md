# Question 15 - Inheritance

## What is the difference between inheritance and composition in C# and when should you use each one?

In C#, *inheritance* and *composition* are two fundamental object-oriented design principles that help to create reusable, maintainable, and well-structured code. Both are used to establish relationships between classes, but they do so in different ways, each with its own strengths and appropriate use cases.

### 1. Inheritance
Inheritance creates an "is-a" relationship between classes, where one class (the subclass or derived class) inherits properties and behaviors from another class (the superclass or base class). This means the subclass has access to the base class’s methods and fields, and it can also override them to provide specific implementations.

#### Use Cases for Inheritance
- When there is a clear hierarchical relationship.
- When you want to extend the functionality of an existing class.
- When polymorphism is needed (e.g., overriding methods for different subclasses).

#### Example of Inheritance in C#
Suppose you have a base class `Animal` and specific types of animals as derived classes, such as `Dog` and `Cat`.

```csharp
using System;

public class Animal
{
    public virtual void Speak()
    {
        Console.WriteLine("The animal makes a sound.");
    }
}

public class Dog : Animal
{
    public override void Speak()
    {
        Console.WriteLine("The dog barks.");
    }
}

public class Cat : Animal
{
    public override void Speak()
    {
        Console.WriteLine("The cat meows.");
    }
}

class Program
{
    static void Main()
    {
        Animal myDog = new Dog();
        Animal myCat = new Cat();
        
        myDog.Speak(); // Output: The dog barks.
        myCat.Speak(); // Output: The cat meows.
    }
}
```

In this example, `Dog` and `Cat` inherit from `Animal` and override the `Speak` method. This allows you to treat both `Dog` and `Cat` objects as `Animal` objects while still getting specific behaviors when calling `Speak`.

### 2. Composition
Composition creates a "has-a" relationship, where a class is composed of one or more objects from other classes. Instead of inheriting behavior, the class uses instances of other classes to perform its functionality. This allows for more flexible designs and easier code maintenance.

#### Use Cases for Composition
- When there is no clear hierarchical relationship, and behaviors can be shared among different classes.
- When you want to achieve polymorphism by delegating behavior instead of inheriting.
- When you want to favor a more modular design, as composition allows you to change parts of the implementation more easily without affecting the entire hierarchy.

#### Example of Composition in C#
Suppose you have a `Car` class that has separate components like an `Engine` and a `Transmission`. You could compose a `Car` object by including instances of these components.

```csharp
using System;

public class Engine
{
    public void Start()
    {
        Console.WriteLine("The engine starts.");
    }
    
    public void Stop()
    {
        Console.WriteLine("The engine stops.");
    }
}

public class Transmission
{
    public void ShiftGear(int gear)
    {
        Console.WriteLine($"Shifting to gear {gear}.");
    }
}

public class Car
{
    private Engine _engine;
    private Transmission _transmission;

    public Car(Engine engine, Transmission transmission)
    {
        _engine = engine;
        _transmission = transmission;
    }

    public void StartCar()
    {
        _engine.Start();
    }
    
    public void ShiftCarGear(int gear)
    {
        _transmission.ShiftGear(gear);
    }
}

class Program
{
    static void Main()
    {
        Engine engine = new Engine();
        Transmission transmission = new Transmission();
        
        Car myCar = new Car(engine, transmission);
        
        myCar.StartCar();            // Output: The engine starts.
        myCar.ShiftCarGear(2);       // Output: Shifting to gear 2.
    }
}
```

In this example, `Car` is composed of an `Engine` and a `Transmission`. `Car` doesn’t inherit from either `Engine` or `Transmission`, but it *has* an engine and a transmission, which allows it to utilize their functionalities through composition.

### When to Use Inheritance vs. Composition

- **Use Inheritance** when:
  - There is a clear, logical "is-a" relationship.
  - You need polymorphic behavior across related classes.
  - Code sharing via inheritance enhances code reuse without introducing excessive complexity.

- **Use Composition** when:
  - You need to create more modular and flexible designs, and there’s a "has-a" relationship.
  - Classes share common behaviors or dependencies that are not naturally suited to a strict inheritance hierarchy.
  - You need to swap parts of a class easily, making the class more flexible and maintainable.

In general, *composition* is often preferred over *inheritance* because it reduces the risk of creating overly rigid structures, especially when behavior or requirements are likely to change. This design principle is known as **"Favor composition over inheritance"** and can lead to more adaptable and scalable code.