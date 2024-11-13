# Question 2 - Clean Code

## Can you explain the SOLID principles of object-oriented programming and how they can be applied to C# code?

The SOLID principles are five design principles in object-oriented programming that help to create more maintainable, flexible, and scalable software. Here's a breakdown of each principle, with C# code examples:

### 1. Single Responsibility Principle (SRP)
A class should only have one reason to change, meaning it should only have one job or responsibility.

**Example**:
```csharp
// Violates SRP: Handles both employee data and salary calculation
public class Employee
{
    public string Name { get; set; }
    public double Salary { get; set; }

    public void CalculateSalary()
    {
        // Logic for salary calculation
    }
}

// Following SRP: Separate responsibilities into different classes
public class Employee
{
    public string Name { get; set; }
}

public class SalaryCalculator
{
    public double CalculateSalary(Employee employee)
    {
        // Salary calculation logic
        return 0; // Placeholder return value
    }
}
```

In this example, `Employee` is responsible only for holding employee data, and `SalaryCalculator` is responsible for calculating salaries, thus each class has a single responsibility.

---

### 2. Open/Closed Principle (OCP)
A class should be open for extension but closed for modification. You should be able to add new functionality without changing existing code.

**Example**:
```csharp
// Violates OCP: Directly modifying the original code to add new features
public class AreaCalculator
{
    public double CalculateRectangleArea(double width, double height) => width * height;

    public double CalculateCircleArea(double radius) => Math.PI * radius * radius;
}

// Following OCP: Using inheritance to extend functionality
public abstract class Shape
{
    public abstract double CalculateArea();
}

public class Rectangle : Shape
{
    public double Width { get; set; }
    public double Height { get; set; }

    public override double CalculateArea() => Width * Height;
}

public class Circle : Shape
{
    public double Radius { get; set; }

    public override double CalculateArea() => Math.PI * Radius * Radius;
}

public class AreaCalculator
{
    public double CalculateArea(Shape shape) => shape.CalculateArea();
}
```

By defining a base `Shape` class, new shapes (e.g., `Triangle`) can be added by creating new classes without modifying `AreaCalculator`.

---

### 3. Liskov Substitution Principle (LSP)
Subtypes must be substitutable for their base types without altering the correctness of the program.

**Example**:
```csharp
// Violates LSP: Square does not behave correctly as a Rectangle subclass
public class Rectangle
{
    public virtual double Width { get; set; }
    public virtual double Height { get; set; }
}

public class Square : Rectangle
{
    public override double Width
    {
        set { base.Width = base.Height = value; }
    }

    public override double Height
    {
        set { base.Width = base.Height = value; }
    }
}

// Following LSP: Separate classes for Rectangle and Square, no inheritance
public abstract class Shape
{
    public abstract double CalculateArea();
}

public class Rectangle : Shape
{
    public double Width { get; set; }
    public double Height { get; set; }

    public override double CalculateArea() => Width * Height;
}

public class Square : Shape
{
    public double Side { get; set; }

    public override double CalculateArea() => Side * Side;
}
```

Here, `Square` does not inherit from `Rectangle` since its behavior (equal width and height) differs. This respects LSP by keeping `Square` and `Rectangle` independent.

---

### 4. Interface Segregation Principle (ISP)
A client should not be forced to implement interfaces it does not use. Split large interfaces into smaller, more specific ones.

**Example**:
```csharp
// Violates ISP: Forcing implementations of unrelated methods
public interface IWorker
{
    void Work();
    void Sleep();
}

public class HumanWorker : IWorker
{
    public void Work() { /* Human work */ }
    public void Sleep() { /* Human sleep */ }
}

public class RobotWorker : IWorker
{
    public void Work() { /* Robot work */ }
    public void Sleep() { /* Robots don’t sleep */ }  // Awkward for robots
}

// Following ISP: Split interfaces into specific functionalities
public interface IWorkable
{
    void Work();
}

public interface ISleepable
{
    void Sleep();
}

public class HumanWorker : IWorkable, ISleepable
{
    public void Work() { /* Human work */ }
    public void Sleep() { /* Human sleep */ }
}

public class RobotWorker : IWorkable
{
    public void Work() { /* Robot work */ }
}
```

Now, `RobotWorker` only implements `IWorkable`, avoiding irrelevant methods and better following ISP.

---

### 5. Dependency Inversion Principle (DIP)
High-level modules should not depend on low-level modules. Both should depend on abstractions. Abstractions should not depend on details, but details should depend on abstractions.

**Example**:
```csharp
// Violates DIP: High-level class directly depends on a low-level class
public class LightBulb
{
    public void TurnOn() { /* Light on */ }
    public void TurnOff() { /* Light off */ }
}

public class Switch
{
    private LightBulb _bulb = new LightBulb();

    public void Operate()
    {
        _bulb.TurnOn();
    }
}

// Following DIP: Switch depends on an abstraction instead of a concrete class
public interface ISwitchable
{
    void TurnOn();
    void TurnOff();
}

public class LightBulb : ISwitchable
{
    public void TurnOn() { /* Light on */ }
    public void TurnOff() { /* Light off */ }
}

public class Switch
{
    private ISwitchable _device;

    public Switch(ISwitchable device)
    {
        _device = device;
    }

    public void Operate()
    {
        _device.TurnOn();
    }
}
```

By depending on `ISwitchable`, `Switch` can work with any device that implements this interface, making it more flexible and respecting DIP.