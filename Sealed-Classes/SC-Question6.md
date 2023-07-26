# Question 6 - Sealed Classes

## Is it possible for a sealed class to be used as a base class in C#?

In C#, a sealed class is a class that cannot be inherited, meaning you cannot create a derived class from it. Therefore, a sealed class cannot be used as a base class for other classes. The primary purpose of a sealed class is to prevent inheritance, usually when the designer of the class believes that it shouldn't be extended or overridden.

Here's an example of a sealed class in C#:

```
public sealed class SealedClass
{
    public void SomeMethod()
    {
        Console.WriteLine("This is a method in the sealed class.");
    }
}

```
Now, if you try to create a derived class from the sealed class, you will get a compilation error:

```
public class DerivedClass : SealedClass // This will cause a compilation error
{
    // Some additional code
}


```
The error message will be something like: "cannot derive from sealed type 'SealedClass'."

However, you can use a sealed class as a normal class, creating instances of it and using its methods and properties, as shown below:

```
class Program
{
    static void Main()
    {
        SealedClass sealedObj = new SealedClass();
        sealedObj.SomeMethod();
    }
}


```
Output:

```
This is a method in the sealed class.

```
Remember that using sealed classes is optional, and it's mostly a design decision. If you create a class with the intent of preventing inheritance, you can mark it as sealed. Otherwise, most classes in C# are not sealed, allowing them to be extended and used as base classes for other classes.

