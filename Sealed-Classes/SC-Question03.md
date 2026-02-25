# Question 3 - Sealed Classes

## What is the difference between a sealed class and an unsealed class in C#?

In C#, a sealed class and an unsealed (or open) class have distinct characteristics related to inheritance and extension. Let's explore the differences between them using examples.

Sealed Class:
A sealed class is a class that cannot be inherited. It's marked with the sealed keyword. This means you cannot create a derived class that inherits from a sealed class.

```
sealed class SealedClass
{
    public void SomeMethod()
    {
        Console.WriteLine("Method in sealed class");
    }
}

class DerivedClass : SealedClass // This will result in a compilation error
{
    // ...
}
```
In this example, attempting to derive a class from SealedClass (DerivedClass in this case) would result in a compilation error.

Unsealed (Open) Class:
An unsealed class is a regular class that can be inherited. By default, all classes in C# are unsealed, meaning they can be used as base classes for other classes.

```
class BaseClass
{
    public virtual void SomeMethod()
    {
        Console.WriteLine("Method in base class");
    }
}

class DerivedClass : BaseClass
{
    public override void SomeMethod()
    {
        Console.WriteLine("Method in derived class");
    }
}

```
In this example, BaseClass is an unsealed class, and you can derive a new class from it (DerivedClass). The virtual keyword in the SomeMethod of the base class allows the method to be overridden in the derived class using the override keyword.

To summarize:

Sealed Class: Cannot be inherited. Marked with the sealed keyword.
Unsealed (Open) Class: Can be inherited. By default, all classes are unsealed unless marked sealed.

Use sealed classes when you want to prevent further derivation from a particular class to maintain control over its behavior and design. Use unsealed classes for normal class hierarchies where you expect other classes to derive from them and extend their functionality.
