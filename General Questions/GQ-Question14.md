# Question 14 - General Questions

## What is an anonymous method in C# and how is it used?

In C#, an anonymous method is a method that does not have a name and is defined inline within the code of another method or expression. It can be used in place of a named method anywhere a delegate is expected. A delegate is an object that can refer to a method and can be passed as a parameter or returned as a value.

Anonymous methods can be defined using the delegate keyword, followed by the argument list and body of the method. For example:

```
delegate (int x, int y) {
    return x + y;
};

```
This anonymous method takes two integer arguments and returns their sum. It can be used as follows:

```
int result = myDelegate(3, 4); // result = 7

```
Where myDelegate is a delegate variable that has been assigned to this anonymous method.

Alternatively, C# also introduced lambda expressions, which are a shorter and more readable syntax for creating anonymous methods. For example, the anonymous method above can be expressed as a lambda expression like this:

```
(x, y) => x + y

```
Anonymous methods are commonly used in event handling and LINQ queries, among other places, where they allow for concise and flexible code.

