# Question 3 - Inheritance

## What is the difference between single inheritance and multiple inheritance in C#?

In object-oriented programming, inheritance is a mechanism that allows a new class (the derived or subclass) to inherit properties and behaviors (fields and methods) from an existing class (the base or superclass). C# supports both single inheritance and multiple inheritance, and each has its own characteristics.

Single Inheritance:
In single inheritance, a class can inherit from only one base class. This promotes a simpler and more straightforward class hierarchy.

```csharp
// Base class
class Animal
{
    public void Eat()
    {
        Console.WriteLine("Animal is eating.");
    }
}

// Derived class inheriting from a single base class
class Dog : Animal
{
    public void Bark()
    {
        Console.WriteLine("Dog is barking.");
    }
}


```
In this example, the class Dog inherits from the single base class Animal. It can access the Eat method from the base class and also has its own method Bark.

Multiple Inheritance:
Multiple inheritance allows a class to inherit from more than one base class. However, C# does not support multiple inheritance of classes (i.e., inheriting from multiple classes). Instead, it supports multiple inheritance through interfaces.

```
// First base interface
interface IDriveable
{
    void Drive();
}

// Second base interface
interface IFlyable
{
    void Fly();
}

// Derived class implementing multiple interfaces
class FlyingCar : IDriveable, IFlyable
{
    public void Drive()
    {
        Console.WriteLine("Flying car is being driven on the road.");
    }

    public void Fly()
    {
        Console.WriteLine("Flying car is taking off and flying.");
    }
}


```
In this example, the class FlyingCar implements both the IDriveable and IFlyable interfaces, effectively achieving a form of multiple inheritance. It can access the methods defined in both interfaces.

It's important to note that C# interfaces provide a way to achieve the benefits of multiple inheritance while avoiding some of the complexities and ambiguities associated with traditional multiple inheritance in other languages like C++.

In summary, single inheritance involves a class inheriting from a single base class, while multiple inheritance can be achieved in C# through interfaces, allowing a class to inherit from multiple interfaces.