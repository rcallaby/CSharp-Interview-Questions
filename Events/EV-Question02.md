# Question 2 - Events

## Can you give an example of how to declare and raise an event in C#?

Here's an example of how to declare and raise an event in C#:

```
using System;

class Program
{
    // Declare the delegate (if using non-generic pattern).
    public delegate void MyEventHandler(object sender, EventArgs e);

    // Declare the event using the delegate.
    public event MyEventHandler MyEvent;

    // This will raise the event.
    protected virtual void OnMyEvent(EventArgs e)
    {
        MyEventHandler handler = MyEvent;
        if (handler != null)
        {
            handler(this, e);
        }
    }

    static void Main()
    {
        Program p = new Program();

        // Add the event handler.
        p.MyEvent += new MyEventHandler(p_MyEvent);

        // Call the method that raises the event.
        p.RaiseMyEvent();
    }

    // The event handler.
    static void p_MyEvent(object sender, EventArgs e)
    {
        Console.WriteLine("MyEvent is raised by: " + sender.ToString());
    }

    // This method raises the event.
    public void RaiseMyEvent()
    {
        OnMyEvent(EventArgs.Empty);
    }
}

```
In this example, we declare an event called MyEvent of type MyEventHandler. The MyEventHandler delegate is defined to take two parameters: an object that represents the sender of the event, and an EventArgs object that contains any additional information about the event.

To raise the event, we define a method called OnMyEvent that takes an EventArgs object as a parameter. This method first checks if there are any event handlers attached to the event (i.e., if MyEvent is not null), and if so, it invokes the event by calling the delegate with the sender object and the EventArgs object.

In the Main method, we create an instance of the Program class and add an event handler to MyEvent by using the += operator. We then call the RaiseMyEvent method, which raises the event and triggers the event handler we added earlier. In this case, the event handler simply writes a message to the console to indicate that the event was raised.