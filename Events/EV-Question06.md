# Question 6 - Events

## What are called combinable delegates?

In the context of programming, delegates are a type that represents references to methods with a particular signature. Combinable delegates, also known as multicast delegates, are a feature found in some programming languages that allow multiple methods to be combined into a single delegate. When the combined delegate is invoked, all the methods subscribed to it will be executed in the order they were added.

Let's illustrate this with an example in C#:

```
using System;

// Declare a delegate with a specific signature
public delegate void MyDelegate(string message);

class Program
{
    static void Main()
    {
        // Create instances of the methods to be combined
        MyDelegate method1 = DisplayMessage;
        MyDelegate method2 = ShowMessage;

        // Create a combinable delegate by combining method1 and method2
        MyDelegate combinedDelegate = method1 + method2;

        // Invoke the combined delegate, which will call both DisplayMessage and ShowMessage
        combinedDelegate("Hello, delegates!");

        // Output:
        // Display Message: Hello, delegates!
        // Show Message: Hello, delegates!
    }

    static void DisplayMessage(string message)
    {
        Console.WriteLine("Display Message: " + message);
    }

    static void ShowMessage(string message)
    {
        Console.WriteLine("Show Message: " + message);
    }
}


```

In the example above, we declare a delegate named MyDelegate, which represents a method taking a string parameter and returning void. Then, we define two methods, DisplayMessage and ShowMessage, both having the same signature as the delegate.

By using the + operator, we combine method1 and method2 into a single delegate named combinedDelegate. When we invoke combinedDelegate, both DisplayMessage and ShowMessage are called one after the other.

This feature is particularly useful in event handling scenarios, where multiple event handlers can be added to a single event delegate to respond to an event.