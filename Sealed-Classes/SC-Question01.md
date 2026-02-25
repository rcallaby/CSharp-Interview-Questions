# Question 1 - Sealed Classes

## What is a sealed class in C# and why is it used?

A sealed class in C# is a class that cannot be inherited or extended by other classes. When you mark a class as "sealed," you are essentially declaring that it is the final, end-point class in an inheritance hierarchy. This means that other classes cannot inherit from it to create subclasses or derived classes.

Here's an example of a sealed class:

```
sealed class SealedClass
{
    public void SomeMethod()
    {
        Console.WriteLine("This is a method in the sealed class.");
    }
}

// This will result in a compilation error because you cannot inherit from a sealed class.
class DerivedClass : SealedClass
{
    // ...
}
```

In this example, SealedClass is marked as sealed, so you cannot create a class that inherits from it, like DerivedClass. Attempting to do so will result in a compilation error.

Sealed classes are used for a few specific reasons:

Security: Sealing a class ensures that it cannot be modified or extended in ways that could compromise its intended behavior or security. This is particularly useful for classes that are part of a security-sensitive framework or library.

Optimization: Sealed classes allow the compiler to make certain performance optimizations because it knows that no derived classes will be created. This can lead to more efficient code execution.

Design control: When you design a class and want to ensure that it's used as-is without any modifications or extensions, you can seal it to enforce that constraint. This can help maintain the integrity of your codebase and prevent unintended changes.

Preventing misuse: Sealed classes can also prevent misuse of your code by discouraging developers from creating unnecessary subclasses or inheriting from classes that shouldn't be extended.

In summary, sealed classes in C# provide a way to restrict inheritance, which can be useful for security, performance, design control, and maintaining the intended use of a class.