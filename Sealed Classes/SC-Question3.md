# Question 3 - Sealed Classes

## What is the difference between a sealed class and an unsealed class in C#?

In C#, a sealed class and an unsealed (or non-sealed) class are two different kinds of classes with different capabilities and restrictions.

An unsealed class is a regular class that can be inherited by other classes. It is the default type of class in C#. An unsealed class can be extended and modified by other classes that derive from it. An unsealed class can also be used as a base class for polymorphism, allowing derived classes to override and provide their own implementation of the base class's methods and properties.

On the other hand, a sealed class is a class that cannot be inherited by other classes. Once a class is marked as sealed, it becomes a leaf class in the inheritance hierarchy, which means it cannot be used as a base class for any other class. The primary purpose of a sealed class is to prevent further inheritance and modifications to its implementation, which can be useful when you want to restrict the behavior of a class to only what has been implemented in it.

In summary, an unsealed class can be inherited and extended by other classes, while a sealed class cannot be inherited or modified further.