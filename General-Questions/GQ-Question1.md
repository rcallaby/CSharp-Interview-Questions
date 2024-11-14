# Question 1 - General Questions

## What is the difference between a method and a function in C#?

In C#, both methods and functions are terms used to describe executable code blocks that can be called to perform specific tasks. However, there's a subtle distinction between the two:

Method:
A method is a code block associated with a class or struct. It defines a set of instructions that can be executed on an instance of the class or struct, or it can be a static method that is associated with the class itself rather than instances of the class. Methods are used to perform actions, manipulate data, or provide functionality related to the class.

Here's an example of a method within a class:

```csharp
public class MathOperations
{
    public int Add(int a, int b)
    {
        return a + b;
    }
}

class Program
{
    static void Main(string[] args)
    {
        MathOperations math = new MathOperations();
        int result = math.Add(5, 3); // Calling the method
        Console.WriteLine(result);   // Output: 8
    }
}


```

In this example, Add is a method defined within the MathOperations class. It takes two integers as parameters and returns their sum.

Function:
In C#, the term "function" is commonly used interchangeably with "method." However, in a broader context, a function is a self-contained block of code that performs a specific task and can return a value. This term is often used in languages that support both procedural programming and object-oriented programming. Since C# is primarily an object-oriented language, the concept of "function" is usually referred to as "method."

So, while the distinction between methods and functions can be blurred, especially in C#, it's more accurate to use "method" when discussing code blocks associated with classes and structs in C#.

To summarize, both methods and functions refer to executable code blocks in C#, but the term "method" is used more commonly in the context of classes and structs, while "function" might be used in a more general programming context.