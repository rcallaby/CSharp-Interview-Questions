# Question 7 - Sealed Class

## Is it possible for a sealed class in C# to define virtual methods?

It is not possible to define a sealed class with virtual methods in C#. The reason for this is that a sealed class is designed to prevent inheritance, and virtual methods are meant to be overridden in derived classes.

When you declare a class as sealed in C#, it means it cannot be inherited, and thus, there would be no derived class to override any virtual methods. This restriction exists to ensure that the behavior of the sealed class remains consistent and cannot be altered or extended by other classes.

Here's an example of how a sealed class is defined in C#:

```
public sealed class SealedClass
{
    public void NonVirtualMethod()
    {
        Console.WriteLine("This is a non-virtual method.");
    }
}

```
If you try to add the virtual keyword to any method in a sealed class, you will encounter a compile-time error.

However, if you want to have a virtual method in a class that can be overridden by its derived classes, you should remove the sealed modifier. Here's an example of a base class with a virtual method:

```
public class BaseClass
{
    public virtual void VirtualMethod()
    {
        Console.WriteLine("This is a virtual method.");
    }
}

```
Derived classes can then override this virtual method as needed:

```
public class DerivedClass : BaseClass
{
    public override void VirtualMethod()
    {
        Console.WriteLine("This is an overridden virtual method in the derived class.");
    }
}

```
In summary, a sealed class in C# cannot define virtual methods, but you can define virtual methods in non-sealed classes to allow for method overriding in derived classes.
