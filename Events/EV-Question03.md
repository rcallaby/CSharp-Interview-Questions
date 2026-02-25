# Question 3 - Events

## What is a delegate in C# and how is it related to events?

In C#, a delegate is a type that represents a method signature, which specifies the return type and the parameters of a method. Delegates can be thought of as a reference to a method that can be passed as an argument to another method, or stored as a field or property.

In the context of events, a delegate is used to define the contract between an event publisher and its subscribers. An event publisher is an object that raises events, while an event subscriber is an object that listens to those events and responds to them. The delegate is used to define the signature of the event handler method, which is the method that will be called by the event publisher when the event is raised.

For example, let's say we have an event named "ButtonClick" in a class called "Button". To define the event handler method for this event, we would create a delegate with the same signature as the event handler method:

```
public delegate void ButtonClickEventHandler(object sender, EventArgs e);

```
Here, the delegate is named "ButtonClickEventHandler" and takes two parameters - an object that represents the event publisher (in this case, the Button object that raised the event), and an instance of the EventArgs class (which contains any additional data that may be relevant to the event).

We can then use this delegate to define the "ButtonClick" event in the "Button" class:

```
public event ButtonClickEventHandler ButtonClick;

```
This code creates an event named "ButtonClick" that is of type "ButtonClickEventHandler". This means that when the event is raised, any subscribers to the event must provide a method that matches the signature of the delegate - that is, a method that takes an object and an EventArgs parameter and returns void.

Subscribers can then subscribe to the event by providing a method that matches the delegate signature and adding it to the event:

```
button.ButtonClick += new ButtonClickEventHandler(HandleButtonClick);

private void HandleButtonClick(object sender, EventArgs e)
{
    // Event handling logic goes here
}

```
Here, the "HandleButtonClick" method matches the delegate signature, so it can be added as a subscriber to the "ButtonClick" event. When the event is raised, the "HandleButtonClick" method will be called with the object that raised the event and any relevant event arguments.