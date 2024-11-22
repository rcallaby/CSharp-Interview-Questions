# Question 30 - General Questions

## What is Dynamic Dispatch in C# and how is it used?

Dynamic dispatch in C# refers to the process where the decision about which method to invoke is made at runtime, rather than compile time. It is used to enable polymorphism, allowing different implementations of a method to be executed depending on the runtime type of the object.

### **How Dynamic Dispatch Works**
Dynamic dispatch primarily occurs when:
1. **Virtual Methods**: Methods are declared with the `virtual` keyword in a base class and overridden in a derived class using the `override` keyword.
2. **Interfaces**: Methods are implemented from an interface.
3. **Dynamic Typing**: The `dynamic` keyword is used to defer method binding to runtime.

When a method is invoked on a reference, the runtime type of the object determines the actual method implementation that gets executed.

### **Key Features**
- **Achieves Polymorphism**: Allows derived classes to provide specific implementations of a method that is defined in a base class.
- **Late Binding**: The actual method to execute is determined at runtime.

---

### **Example: Using Virtual Methods**

```csharp
using System;

public class Animal
{
    public virtual void Speak()
    {
        Console.WriteLine("Animal speaks");
    }
}

public class Dog : Animal
{
    public override void Speak()
    {
        Console.WriteLine("Dog barks");
    }
}

public class Cat : Animal
{
    public override void Speak()
    {
        Console.WriteLine("Cat meows");
    }
}

class Program
{
    static void Main()
    {
        Animal myAnimal = new Dog();
        myAnimal.Speak(); // Output: Dog barks

        myAnimal = new Cat();
        myAnimal.Speak(); // Output: Cat meows
    }
}
```

Here, `myAnimal.Speak()` uses dynamic dispatch to call the appropriate `Speak` method depending on the runtime type of `myAnimal`.

---

### **Example: Using the `dynamic` Keyword**

The `dynamic` keyword allows method resolution at runtime, bypassing compile-time type checking.

```csharp
using System;

class Program
{
    static void Main()
    {
        dynamic value = "Hello";
        Console.WriteLine(value.Length); // Output: 5
        
        value = 42;
        Console.WriteLine(value + 10); // Output: 52
    }
}
```

In this example, the `dynamic` keyword defers type checking and method resolution to runtime.

---

### **When to Use Dynamic Dispatch**
1. **Virtual Methods and Polymorphism**: Use when designing a system with a shared base class and specific behaviors in derived classes.
2. **Dynamic Typing**: Use `dynamic` when interacting with objects whose types are not known at compile time, such as data from external libraries (e.g., COM objects, reflection).
3. **Interfaces**: Use when working with interface references to invoke methods implemented by the underlying runtime type.

### **Caveats**
1. **Performance Overhead**: Dynamic dispatch involves a small performance cost because the method resolution happens at runtime.
2. **Type Safety**: Using `dynamic` can introduce runtime errors that would otherwise be caught at compile time.

Dynamic dispatch is a powerful mechanism in C# for writing flexible and extensible code, but it should be used judiciously to balance performance and type safety.