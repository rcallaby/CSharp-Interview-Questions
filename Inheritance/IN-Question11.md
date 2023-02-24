# Question 11 - Inheritance

## What is the purpose of the base keyword in C#, and how is it used in inheritance?

In C#, the base keyword is used to refer to the base class of the current class. It is used to access members of the base class, such as methods, properties, and fields.

In inheritance, the base keyword is used to call a constructor of the base class from a derived class. When a derived class is instantiated, its constructor must call a constructor of the base class to initialize the base class members. This can be done using the base keyword followed by the constructor parameters.

For example, consider the following code:

```
public class Vehicle
{
    public int NumWheels { get; set; }

    public Vehicle(int numWheels)
    {
        NumWheels = numWheels;
    }
}

public class Car : Vehicle
{
    public string Make { get; set; }

    public Car(int numWheels, string make) : base(numWheels)
    {
        Make = make;
    }
}

```
In this example, Vehicle is the base class and Car is the derived class. The Car constructor takes two parameters, numWheels and make, and calls the base class constructor using the base keyword with the numWheels parameter. This initializes the NumWheels property of the Vehicle base class. The Make property of the Car derived class is initialized separately.

By using the base keyword, we can ensure that the base class is properly initialized before any derived class-specific initialization takes place.