# Question 3 - Generic Types

## Can you explain the difference between a generic class and a non-generic class in C#?

In C#, a generic class is a class that is parameterized by one or more type parameters. These type parameters are defined within angle brackets (<>) after the class name, and can be used to specify the type of data that the class will operate on. For example, the following is an example of a generic class in C# that operates on a type parameter T:

```
public class MyGenericClass<T>
{
    private T myVariable;

    public MyGenericClass(T value)
    {
        myVariable = value;
    }

    public T MyMethod()
    {
        return myVariable;
    }
}

```
A non-generic class, on the other hand, does not have any type parameters and operates on a fixed data type. For example, the following is an example of a non-generic class in C# that operates on an integer:

```
public class MyNonGenericClass
{
    private int myVariable;

    public MyNonGenericClass(int value)
    {
        myVariable = value;
    }

    public int MyMethod()
    {
        return myVariable;
    }
}

```
The main difference between generic and non-generic classes is that generic classes can operate on any type of data, while non-generic classes are restricted to a specific data type. This makes generic classes more flexible and reusable, since they can be used to operate on different types of data without having to create separate classes for each data type. Additionally, generic classes allow for type safety at compile time, since the type of data that they operate on is known at compile time.