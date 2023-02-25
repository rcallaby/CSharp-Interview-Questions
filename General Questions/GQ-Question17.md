# Question 17 - General Questions

## What is an extension method in C# and how is it implemented?

An extension method in C# is a static method that allows you to extend the functionality of an existing type without modifying the type's original source code.

The syntax for defining an extension method is to define a static class with a static method that takes the extended type as its first parameter. This first parameter is marked with the "this" keyword to indicate that it is the type being extended.

Here's an example of an extension method that adds a "Reverse" method to the string type:

```
public static class StringExtensions
{
    public static string Reverse(this string str)
    {
        char[] charArray = str.ToCharArray();
        Array.Reverse(charArray);
        return new string(charArray);
    }
}

```
In this example, the "Reverse" method takes a string as its first parameter (marked with the "this" keyword) and returns a reversed version of the string.

To use this extension method, you simply need to include the namespace that contains the extension method and call it on an instance of the extended type, as if it were a member method of that type:

```
using ExtensionMethods;

string original = "Hello, world!";
string reversed = original.Reverse();

Console.WriteLine(reversed); // Outputs: "!dlrow ,olleH"

```
In this example, the "Reverse" method is called on a string instance ("original") and returns a new string instance with the reversed content.