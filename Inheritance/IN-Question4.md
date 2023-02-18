# Question 4 - Inheritance

## How can you use inheritance to extend an existing class in C#?

In C#, you can use inheritance to extend an existing class by creating a new class that inherits from the existing class. Here are the steps to do so:

Define the parent class: Start by defining the existing class that you want to extend. This class is often referred to as the "base class" or the "parent class".

```
public class ParentClass
{
    // fields, properties, and methods of the parent class
}

```
Define the child class: Create a new class that inherits from the parent class using the : symbol, followed by the name of the parent class.

```
public class ChildClass : ParentClass
{
    // fields, properties, and methods of the child class
}

```
Add new functionality: Now you can add new fields, properties, and methods to the child class that were not present in the parent class. The child class can also override or extend existing methods and properties of the parent class.

```
public class ChildClass : ParentClass
{
    public int NewField { get; set; }

    public void NewMethod()
    {
        // new functionality
    }

    public override void ExistingMethod()
    {
        base.ExistingMethod(); // calling the method of the parent class
        // additional functionality
    }
}

```
By using inheritance, you can reuse the code from the parent class and add new functionality to the child class, without having to rewrite the existing code in the parent class.