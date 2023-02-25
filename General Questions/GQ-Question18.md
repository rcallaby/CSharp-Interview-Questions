# Question 18 - General Questions 

## Can you explain the difference between a method and an operator in C#?

In C#, both methods and operators are used to perform operations on data, but they differ in how they are defined and used.

A method is a block of code that can be called by its name to perform a specific task. It can take input parameters, perform operations, and return a result. Methods are defined as part of a class, and they can be called on instances of that class or on the class itself.

For example, consider the following method that takes two integers as input and returns their sum:

```
public int Add(int a, int b)
{
    return a + b;
}

```
This method can be called like this:

```
int result = Add(5, 10); // result will be 15

```
An operator, on the other hand, is a special symbol or keyword that performs a specific operation on one or more operands. Operators are predefined in C# and can be used with built-in types, user-defined types, and enumerations.

For example, the addition operator "+" is used to add two numeric values together, like this:

```
int result = 5 + 10; // result will be 15

```
Operators can also be overloaded, which means that you can define new behavior for an existing operator when it is used with your own types.

For example, you could define a new "+" operator for a custom Vector class that adds two vectors together component-wise:

```
public static Vector operator +(Vector a, Vector b)
{
    return new Vector(a.X + b.X, a.Y + b.Y, a.Z + b.Z);
}

```
This would allow you to add two vectors like this:

```
Vector result = vector1 + vector2;

```


In summary, methods and operators are both used to perform operations on data in C#, but methods are defined as blocks of code that can be called by name, while operators are special symbols or keywords that perform specific operations on one or more operands.