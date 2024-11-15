# Question 14 - Inheritance

## How do you handle constructor inheritance in C#, and what is the role of the base keyword in constructor inheritance?

In C#, constructor inheritance is handled through the use of the base keyword. The base keyword allows a derived class to call a constructor from its base class. This is useful when the base class has state or behavior that needs to be initialized before the derived class can be constructed.

To inherit a constructor from a base class, the derived class must include a constructor that calls the base constructor using the base keyword. Here's an example:

```csharp
public class MyBaseClass
{
    private int myInt;

    public MyBaseClass(int myInt)
    {
        this.myInt = myInt;
    }
}

public class MyDerivedClass : MyBaseClass
{
    public MyDerivedClass(int myInt) : base(myInt)
    {
        // Additional initialization code for the derived class can be added here
    }
}

```
In this example, MyBaseClass has a constructor that takes an integer argument and initializes the private field myInt. MyDerivedClass inherits from MyBaseClass and includes a constructor that takes an integer argument. The MyDerivedClass constructor calls the MyBaseClass constructor using the base keyword, passing in the integer argument. This initializes the myInt field in the base class, which can then be used by the derived class.

It's important to note that if the base class has multiple constructors, the derived class must call one of them using the base keyword in each of its constructors.

Constructor inheritance allows derived classes to reuse code from their base classes and can help to reduce code duplication. The base keyword is used to call the appropriate constructor in the base class and ensure that the base class's state is properly initialized before the derived class is constructed.