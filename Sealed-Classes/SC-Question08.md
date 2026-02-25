# Question 8 - Sealed Classes

## Is it possible for a non-child class to define sealed methods in C#? 

In C#, the sealed keyword is used to prevent further derivation of a class and to indicate that a method cannot be overridden by any derived class. However, the sealed keyword is typically used with classes to prevent inheritance, not with methods.

Methods in C# are virtual by default, which means they can be overridden by derived classes unless they are marked with the sealed keyword. However, the sealed keyword is used at the class level to prevent inheritance, not at the method level to prevent method overriding.

Here's an example of using the sealed keyword with a class to prevent inheritance:

```
public class BaseClass
{
    public virtual void SomeMethod()
    {
        Console.WriteLine("BaseClass: SomeMethod");
    }
}

public sealed class SealedClass : BaseClass
{
    public override void SomeMethod()
    {
        Console.WriteLine("SealedClass: SomeMethod");
    }
}

// This class cannot be defined since SealedClass is sealed
//public class DerivedClass : SealedClass
//{
//}

```
In the example above, the SealedClass is marked as sealed, so it cannot be further derived from. The SomeMethod method in SealedClass is marked with the override keyword, indicating that it overrides the virtual method defined in the BaseClass.

Remember that the sealed keyword is applied at the class level, not at the method level. If you want to prevent a method from being overridden, you can achieve that by not marking the method as virtual or abstract in the first place. There's no need to use the sealed keyword with methods.