# Question 2 - Generic Types

## How can you create a generic class in C#?

In C#, you can create a generic class by using the angle bracket notation to define a type parameter. A type parameter is a placeholder for a specific type that will be used when the class is instantiated. Here's an example of a generic class:

```
public class MyGenericClass<T>
{
    private T myVariable;

    public MyGenericClass(T variable)
    {
        myVariable = variable;
    }

    public T GetVariable()
    {
        return myVariable;
    }
}

```
In this example, the T is a type parameter that will be replaced with a specific type when the class is instantiated. The class has a single member variable, myVariable, of type T. The constructor takes a parameter of type T, and the GetVariable method returns the value of myVariable.

To use this generic class, you can create an instance of it with a specific type, like this:

```
MyGenericClass<int> myIntClass = new MyGenericClass<int>(42);
int myInt = myIntClass.GetVariable(); // returns 42

```
In this example, we've instantiated the MyGenericClass with the type parameter int, and passed in the value 42 to the constructor. We then call the GetVariable method to retrieve the value, which is returned as an int.