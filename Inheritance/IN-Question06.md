# Question 6 - Inheritance

## How can you use the "base" keyword in C# to call the base class constructor?

In C#, you can use the base keyword to call the constructor of a base class from a derived class. Here is the syntax for using the base keyword to call a base class constructor:

```
public class DerivedClass : BaseClass
{
    public DerivedClass(args) : base(args)
    {
        // constructor body
    }
}

```
In this example, DerivedClass is derived from BaseClass, and the constructor of DerivedClass is calling the constructor of BaseClass using the base keyword.

Note that the base(args) call must be the first statement in the derived class constructor. This is because the base class constructor needs to be called before any other initialization can be done in the derived class constructor.

You can also use the base keyword to call methods and access properties of the base class from the derived class. For example:

```
public class DerivedClass : BaseClass
{
    public DerivedClass(args)
    {
        base.MethodInBaseClass();
        int value = base.PropertyInBaseClass;
    }
}

```
In this example, MethodInBaseClass() is a method defined in BaseClass, and PropertyInBaseClass is a property defined in BaseClass. The base keyword is used to access these members from the derived class.