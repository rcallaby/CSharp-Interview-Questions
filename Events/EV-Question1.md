# Question 1 - Events

## What is an event in C# and how does it work?

In C#, an event is a mechanism that enables objects to communicate with each other by signaling that an action has occurred. Essentially, an event is a notification that something has happened that other parts of the program may be interested in.

To define an event, you need to use the event keyword in combination with a delegate type that defines the signature of the event. The delegate type specifies the method signature for the event handlers that can be attached to the event. For example:

```
public delegate void EventHandler(object sender, EventArgs e);

public class MyClass
{
    public event EventHandler MyEvent;
}

```
In this example, the MyClass has an event called MyEvent that is of type EventHandler. The EventHandler delegate is a pre-defined delegate type that takes two parameters: an object that represents the object that raised the event (in this case, MyClass), and an EventArgs object that contains any additional information about the event.

To raise the event, you can invoke it like a regular method:

```
MyEvent?.Invoke(this, EventArgs.Empty);

```
In this example, the ? after MyEvent ensures that the event is only invoked if there are any handlers attached to it.

To handle the event, you can attach a method to the event using the += operator:

```
MyClass obj = new MyClass();
obj.MyEvent += MyEventHandler;

```
In this example, MyEventHandler is a method that has the same signature as the EventHandler delegate. When MyEvent is raised, the MyEventHandler method will be called with the appropriate arguments.