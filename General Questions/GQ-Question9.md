# Question 9 -General Questions

## What is a sealed class in C# and why is it used?

In C#, a sealed class is a class that cannot be inherited by other classes. When a class is marked as sealed, it means that it is complete and cannot be extended further.

The main reason to use a sealed class is to prevent the class from being modified or extended by other developers. This is useful when you want to ensure that the class works as intended and cannot be altered in unexpected ways. Sealed classes are also useful for performance reasons, as they can be optimized more effectively by the compiler.

Here are a few other things to note about sealed classes in C#:

Sealed classes can still inherit from other classes, but they cannot be inherited by other classes.
Sealed methods can still be overridden by derived classes, but sealed classes cannot be inherited by derived classes.
It's best practice to mark a class as sealed if it is intended to be used as a standalone class and not be inherited.
Here's an example of a sealed class in C#:

```
sealed class MySealedClass
{
    // class members
}

```
In this example, MySealedClass is marked as sealed, which means that no other class can inherit from it.