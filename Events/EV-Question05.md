# Question 5 - Events

## Can you explain the difference between an event and a delegate in C#?

In C#, both events and delegates are important concepts related to handling and raising events, but they serve slightly different purposes. Let's delve into the differences between events and delegates with examples.

### Delegates:

A delegate is a type that defines a method signature, allowing you to encapsulate a reference to a method and invoke it through the delegate. Delegates are often used to create callback mechanisms, where a method can be passed around and executed by other parts of the code.

Here's a basic example of using a delegate:

```
public delegate void MyDelegate(string message);

public class MyClass
{
    public void PrintMessage(string message)
    {
        Console.WriteLine(message);
    }
}

class Program
{
    static void Main()
    {
        MyClass myObj = new MyClass();
        MyDelegate myDelegate = myObj.PrintMessage;

        myDelegate("Hello, delegates!");
    }
}
```
In this example, MyDelegate is defined as a delegate type that takes a string parameter. An instance of MyClass is created, and the PrintMessage method is assigned to the delegate. Later, the delegate is invoked with a message, leading to the execution of the PrintMessage method.

### Events:

An event is a mechanism for one class (the publisher or sender) to notify other classes (subscribers or listeners) when something of interest happens. Events are based on delegates but provide a level of encapsulation and control over how subscribers can interact with the event.

Here's an example of using an event:

```
public class EventPublisher
{
    public event EventHandler SomethingHappened;

    public void DoSomething()
    {
        Console.WriteLine("Something is happening...");
        OnSomethingHappened();
    }

    protected virtual void OnSomethingHappened()
    {
        SomethingHappened?.Invoke(this, EventArgs.Empty);
    }
}

public class EventSubscriber
{
    public void HandleEvent(object sender, EventArgs e)
    {
        Console.WriteLine("Event handled by subscriber");
    }
}

class Program
{
    static void Main()
    {
        EventPublisher publisher = new EventPublisher();
        EventSubscriber subscriber = new EventSubscriber();

        publisher.SomethingHappened += subscriber.HandleEvent;

        publisher.DoSomething();
    }
}
```
In this example, EventPublisher defines an event called SomethingHappened. When the DoSomething method is called, it invokes the event, notifying any subscribed event handlers. The EventSubscriber class has a method HandleEvent that is assigned to the event handler. When DoSomething is called, the subscriber's event handler method is executed.

In summary, delegates are about method references and can be used for general-purpose callback mechanisms, while events build upon delegates to provide a structured way to handle notifications and interactions between different parts of a program.