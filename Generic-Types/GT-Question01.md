# Question 1 - Generic Types

## What is a generic type in C#?

A generic type in C# is a type that is defined with one or more type parameters, which can be used to specify the type of data that will be used with the generic type. The type parameters are represented by placeholders, usually indicated by angle brackets "<>".

Here's an example of a generic type in C#:

```
public class Stack<T>
{
    private T[] items;
    private int top;

    public Stack()
    {
        items = new T[100];
        top = -1;
    }

    public void Push(T item)
    {
        items[++top] = item;
    }

    public T Pop()
    {
        return items[top--];
    }
}

```
In this example, the Stack<T> class is a generic type that takes a type parameter T. The T is used to represent the type of the items that will be stored in the stack. The class contains methods that allow you to push and pop items onto and off of the stack, respectively. When you create an instance of the Stack<T> class, you can specify the actual type that will be used for T, for example:

```
Stack<int> intStack = new Stack<int>();
intStack.Push(1);
intStack.Push(2);
intStack.Push(3);
intStack.Pop(); // returns 3

```
In this case, the type parameter T is replaced with int, so the stack can only contain integer values.