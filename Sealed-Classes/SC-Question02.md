# Question 2 - Sealed Classes

## Can you give an example of how to declare a sealed class in C#?

Here's an example of how to declare a sealed class in C#:

```
public sealed class MySealedClass
{
    // class members
}
```
In this example, MySealedClass is a sealed class. The sealed keyword is used to indicate that the class cannot be inherited by other classes. This means that you cannot create a subclass or derived class from this class.

By sealing a class, you ensure that the implementation of the class is final and cannot be changed by other classes. This can be useful for security reasons, or to ensure that the behavior of the class remains consistent and predictable.
