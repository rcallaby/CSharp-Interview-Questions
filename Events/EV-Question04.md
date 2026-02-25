# Question 4 - Events

## How can you subscribe and unsubscribe to an event in C#?

In C#, you can subscribe to and unsubscribe from events using the event keyword and the += and -= operators, respectively.

Here's an example of how to subscribe to an event:

```
// define a class with an event
public class ExampleClass
{
    public event EventHandler MyEvent;

    // method that raises the event
    protected void OnMyEvent()
    {
        if (MyEvent != null)
        {
            MyEvent(this, EventArgs.Empty);
        }
    }
}

// subscribe to the event
ExampleClass exampleObject = new ExampleClass();
exampleObject.MyEvent += HandleMyEvent;

// event handler method
void HandleMyEvent(object sender, EventArgs e)
{
    Console.WriteLine("Event raised!");
}

```
In this example, the ExampleClass defines an event called MyEvent using the event keyword. To subscribe to the event, we create an instance of the class and use the += operator to attach the HandleMyEvent method to the event. The HandleMyEvent method will be called when MyEvent is raised.

To unsubscribe from the event, we can use the -= operator:

```
// unsubscribe from the event
exampleObject.MyEvent -= HandleMyEvent;
```
This will remove the HandleMyEvent method from the list of event handlers that will be called when MyEvent is raised.
