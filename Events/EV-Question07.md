# Question 7 - Events

## How to use Delegates with Events? 

In C#, delegates and events are used together to implement the Observer design pattern, which allows one object (the publisher) to notify other objects (the subscribers) when something of interest happens. Delegates are function pointers that allow you to reference methods, and events provide a layer of encapsulation and safety for working with delegates.

Let's go through a step-by-step guide on how to use delegates with events with an example:

Step 1: Declare a Delegate
First, you need to declare a delegate that specifies the method signature of the event handlers. The delegate acts as a contract for the methods that can be subscribed to the event.

```
public delegate void EventHandlerDelegate(string message);

```

Step 2: Declare an Event
After declaring the delegate, you can declare an event based on that delegate inside a class. The event provides an interface for adding and removing event handlers and ensures that only the owning class can raise the event.

```
public class EventPublisher
{
    public event EventHandlerDelegate EventOccurred;
}

```

Step 3: Raise the Event
In your publisher class, whenever an event occurs that you want to notify subscribers about, you can raise the event. It's common to create a method that raises the event.

```
public class EventPublisher
{
    public event EventHandlerDelegate EventOccurred;

    public void RaiseEvent(string message)
    {
        if (EventOccurred != null)
        {
            EventOccurred(message);
        }
    }
}

```
Step 4: Subscribe to the Event
In your subscriber classes, you can subscribe to the event by providing a method that matches the delegate's signature. This method will be called when the event is raised.

```
public class EventSubscriber
{
    public void HandleEvent(string message)
    {
        Console.WriteLine("EventSubscriber: Event occurred with message - " + message);
    }
}


```
Step 5: Putting It All Together
Now, let's put everything together and demonstrate how to use delegates with events:

```
using System;

public delegate void EventHandlerDelegate(string message);

public class EventPublisher
{
    public event EventHandlerDelegate EventOccurred;

    public void RaiseEvent(string message)
    {
        if (EventOccurred != null)
        {
            EventOccurred(message);
        }
    }
}

public class EventSubscriber
{
    public void HandleEvent(string message)
    {
        Console.WriteLine("EventSubscriber: Event occurred with message - " + message);
    }
}

public class Program
{
    static void Main()
    {
        EventPublisher publisher = new EventPublisher();
        EventSubscriber subscriber1 = new EventSubscriber();
        EventSubscriber subscriber2 = new EventSubscriber();

        // Subscribe to the event
        publisher.EventOccurred += subscriber1.HandleEvent;
        publisher.EventOccurred += subscriber2.HandleEvent;

        // Raise the event
        publisher.RaiseEvent("Hello, delegates and events!");

        // Unsubscribe from the event
        publisher.EventOccurred -= subscriber2.HandleEvent;

        // Raise the event again
        publisher.RaiseEvent("Event again!");

        // Output:
        // EventSubscriber: Event occurred with message - Hello, delegates and events!
        // EventSubscriber: Event occurred with message - Hello, delegates and events!
        // EventSubscriber: Event occurred with message - Event again!
    }
}


```

In this example, the EventPublisher class has an event called EventOccurred, and the EventSubscriber class has a method called HandleEvent, which matches the delegate's signature. When the RaiseEvent method is called on the EventPublisher, both subscriber methods are called, and they receive the message passed in the event.

Remember that events provide a layer of encapsulation and safety by not allowing direct access to the delegate from outside the owning class. Instead, outside classes can only subscribe and unsubscribe from the event, which helps maintain better control over event handling and prevents accidental removal of event handlers by unrelated code.