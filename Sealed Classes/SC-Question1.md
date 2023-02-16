# Question 1 - Sealed Classes

## What is a sealed class in C# and why is it used?

In C#, a sealed class is a class that cannot be inherited by any other class. It is marked with the "sealed" keyword in the class declaration. Once a class is sealed, it cannot be used as a base class for any other class.

Sealed classes are often used to restrict the inheritance hierarchy of a class or to prevent other developers from modifying or extending the class's behavior. By sealing a class, you ensure that its behavior and design remain consistent and predictable, and you avoid unintended side effects that can arise from allowing it to be inherited.

In addition, sealed classes can also provide performance benefits. Since sealed classes cannot be inherited, the compiler can make certain optimizations that would not be possible with non-sealed classes.

It's important to note that while a sealed class cannot be inherited, it can still implement interfaces, contain methods and properties, and have instances created. It is just limited to be extended or modified by other classes.