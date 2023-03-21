# Question 17 - Design Patterns

## What is the Chain of Responsibility pattern in C# and how is it used to handle events in a loosely coupled manner?

The Chain of Responsibility pattern is a behavioral design pattern that is used to process a request or handle an event in an object-oriented system. It provides a way to pass a request through a series of handlers or objects, each of which has the opportunity to process the request.

In C#, this pattern can be implemented by defining a chain of objects, where each object contains a reference to the next object in the chain. When an event occurs, the request is sent to the first object in the chain. If that object can't handle the request, it passes it to the next object, and so on. This creates a loosely coupled system, as each object in the chain only needs to know about the next object in the chain, not about the objects further down the chain.

To implement the Chain of Responsibility pattern in C#, you can define an abstract base class that defines the common interface for all objects in the chain. This base class should have a method to set the next object in the chain, and another method to process the request. Concrete implementations of this class can then be created to handle specific types of requests.

Here is an example of how the Chain of Responsibility pattern can be implemented in C# to handle events in a loosely coupled manner:

```
public abstract class Handler
{
    protected Handler _nextHandler;

    public void SetNextHandler(Handler nextHandler)
    {
        _nextHandler = nextHandler;
    }

    public abstract void HandleRequest(string request);
}

public class ConcreteHandlerA : Handler
{
    public override void HandleRequest(string request)
    {
        if (request == "Request A")
        {
            Console.WriteLine("Request A handled by ConcreteHandlerA");
        }
        else
        {
            _nextHandler?.HandleRequest(request);
        }
    }
}

public class ConcreteHandlerB : Handler
{
    public override void HandleRequest(string request)
    {
        if (request == "Request B")
        {
            Console.WriteLine("Request B handled by ConcreteHandlerB");
        }
        else
        {
            _nextHandler?.HandleRequest(request);
        }
    }
}

// Client code
var handlerA = new ConcreteHandlerA();
var handlerB = new ConcreteHandlerB();
handlerA.SetNextHandler(handlerB);

handlerA.HandleRequest("Request A"); // Output: Request A handled by ConcreteHandlerA
handlerA.HandleRequest("Request B"); // Output: Request B handled by ConcreteHandlerB
handlerA.HandleRequest("Request C"); // Output: (Nothing)

```
In this example, the Chain of Responsibility pattern is used to handle two types of requests ("Request A" and "Request B"). The client code creates two concrete handler objects, ConcreteHandlerA and ConcreteHandlerB, and sets the next handler in the chain using the SetNextHandler method. When the HandleRequest method is called, the request is passed through the chain of handlers until it is handled or until the end of the chain is reached.