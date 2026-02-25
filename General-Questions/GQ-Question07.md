# Question 7 - General Questions

## Can you explain the difference between an abstract class and an interface in C#?

#### **1. Abstract Class:**
An abstract class is a blueprint for other classes. It can contain both abstract members (without implementation) and concrete members (with implementation). Abstract classes serve as base classes and are used to provide common functionality to derived classes.

**Key Features:**
- **Inheritance:** Supports single inheritance; a class can inherit from only one abstract class.
- **Members:** Can include fields, properties, methods, events, and constructors. Both abstract and concrete members are allowed.
- **Access Modifiers:** Members can have access modifiers (e.g., `public`, `protected`, `private`).
- **Purpose:** Used when there is a "is-a" relationship and shared implementation logic.

**Syntax Example:**

```csharp
// Abstract Class Example
public abstract class Animal
{
    // Abstract method (no implementation)
    public abstract void MakeSound();

    // Concrete method
    public void Sleep()
    {
        Console.WriteLine("Sleeping...");
    }
}

public class Dog : Animal
{
    // Implementing abstract method
    public override void MakeSound()
    {
        Console.WriteLine("Woof! Woof!");
    }
}
```

**Usage:**

```csharp
Animal myDog = new Dog();
myDog.MakeSound();  // Outputs: Woof! Woof!
myDog.Sleep();      // Outputs: Sleeping...
```

---

#### **2. Interface:**
An interface defines a contract for classes to implement. It contains only the signatures of methods, properties, events, or indexers without any implementation.

**Key Features:**
- **Multiple Inheritance:** A class can implement multiple interfaces.
- **Members:** Cannot include fields or concrete members; all members are implicitly `public` and abstract.
- **Access Modifiers:** Members cannot have access modifiers; they are always `public`.
- **Purpose:** Used when there is a "can-do" relationship or when you want to define a strict contract.

**Syntax Example:**

```csharp
// Interface Example
public interface IAnimal
{
    // Abstract methods
    void MakeSound();
    void Sleep();
}

public class Cat : IAnimal
{
    // Implementing interface methods
    public void MakeSound()
    {
        Console.WriteLine("Meow! Meow!");
    }

    public void Sleep()
    {
        Console.WriteLine("Sleeping like a cat...");
    }
}
```

**Usage:**

```csharp
IAnimal myCat = new Cat();
myCat.MakeSound();  // Outputs: Meow! Meow!
myCat.Sleep();      // Outputs: Sleeping like a cat...
```

---

#### **Key Differences**

| Feature                   | Abstract Class                          | Interface                         |
|---------------------------|-----------------------------------------|-----------------------------------|
| **Implementation**         | Can include concrete methods and fields. | Cannot include concrete methods or fields. |
| **Inheritance**            | Single inheritance allowed.            | Multiple inheritance allowed.     |
| **Access Modifiers**       | Members can have any access modifier.   | All members are implicitly `public`. |
| **Constructors**           | Can have constructors.                 | Cannot have constructors.         |
| **Usage Scenario**         | Use for shared behavior or base class.  | Use for defining a contract.      |

---

### **Example Combining Both**

```csharp
// Abstract Class
public abstract class Vehicle
{
    public abstract void Drive();
    public void Refuel() => Console.WriteLine("Refueling...");
}

// Interface
public interface IAdvancedVehicle
{
    void SelfPark();
}

// Concrete Class Implementing Both
public class Tesla : Vehicle, IAdvancedVehicle
{
    public override void Drive()
    {
        Console.WriteLine("Driving a Tesla!");
    }

    public void SelfPark()
    {
        Console.WriteLine("Tesla is self-parking...");
    }
}

// Usage
Vehicle myCar = new Tesla();
myCar.Drive();  // Outputs: Driving a Tesla!
myCar.Refuel(); // Outputs: Refueling...

IAdvancedVehicle myAdvancedCar = new Tesla();
myAdvancedCar.SelfPark();  // Outputs: Tesla is self-parking...
```

This example demonstrates how abstract classes and interfaces can be used together to define rich and reusable behavior.
