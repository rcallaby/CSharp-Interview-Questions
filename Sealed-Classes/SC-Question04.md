# Question 4 - Sealed Classes

## How can you use a sealed class to prevent inheritance in C#?

In C#, a sealed class is a class that cannot be inherited by other classes. To prevent inheritance, you can declare a class as sealed using the sealed keyword. Here's an example:

```
public sealed class MyClass
{
    // class members
}

```
In the example above, the MyClass class is declared as sealed, which means it cannot be inherited by other classes.

By marking a class as sealed, you prevent other developers from creating derived classes that inherit from it. This can be useful in situations where you want to maintain control over how your class is used, and ensure that it is not extended in a way that could break its behavior.

It's worth noting that while a sealed class cannot be inherited, it can still be used as a base class for other classes. Additionally, it's important to keep in mind that the sealed keyword only prevents inheritance; it doesn't prevent a developer from creating an instance of the class and using its public members.