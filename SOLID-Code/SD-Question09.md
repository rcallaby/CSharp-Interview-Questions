# Question 9 - SOLID

## How can you use Interfaces in C# to reduce coupling and improve maintainability?

In C#, interfaces are a powerful tool for reducing coupling and improving maintainability in your codebase. Interfaces define a contract that classes must adhere to, allowing you to work with objects without needing to know their specific implementations. This helps decouple components, making your code more flexible, modular, and easier to maintain. Let's go through an example to illustrate how interfaces achieve this:

Suppose you're building a simple application that involves different types of vehicles: cars and bicycles. Instead of directly coupling your code to specific implementations of these vehicles, you can use interfaces to define a common contract for all vehicles.

```
// Define an interface for vehicles
public interface IVehicle
{
    void Start();
    void Stop();
}

// Car class implementing the IVehicle interface
public class Car : IVehicle
{
    public void Start()
    {
        Console.WriteLine("Car started.");
    }

    public void Stop()
    {
        Console.WriteLine("Car stopped.");
    }
}

// Bicycle class implementing the IVehicle interface
public class Bicycle : IVehicle
{
    public void Start()
    {
        Console.WriteLine("Bicycle started pedaling.");
    }

    public void Stop()
    {
        Console.WriteLine("Bicycle stopped pedaling.");
    }
}
```

With the interface IVehicle defined, both Car and Bicycle classes implement this interface. This means they must provide implementations for the Start() and Stop() methods. Now, you can use these classes without tightly coupling your code to their implementations:

```
class Program
{
    static void Main(string[] args)
    {
        IVehicle car = new Car();
        IVehicle bicycle = new Bicycle();

        // Start and stop the vehicles without knowing their specific types
        StartAndStopVehicle(car);
        StartAndStopVehicle(bicycle);
    }

    static void StartAndStopVehicle(IVehicle vehicle)
    {
        vehicle.Start();
        // Some other actions...
        vehicle.Stop();
    }
}
```

In this example, the StartAndStopVehicle method can work with any object that implements the IVehicle interface. This means you can easily add new vehicle types without needing to modify the existing code that uses the StartAndStopVehicle method. This separation of concerns improves code maintainability and allows for easy extensibility.

To sum up, using interfaces in C# helps reduce coupling by allowing you to interact with objects based on their behaviors rather than their concrete types. This enables more modular and maintainable code as you can introduce new implementations without affecting existing code that relies on the interface contract.