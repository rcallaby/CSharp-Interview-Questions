# Question 13 - General Questions

## What is an event in C# and how is it different from a delegate?

In C#, an event is a mechanism that allows an object to notify other objects when something happens, typically in response to some action or state change. An event is declared using the event keyword and is associated with a delegate that defines the signature of the event handler method(s).

A delegate, on the other hand, is a type that represents a reference to a method that has a particular signature. It can be used to pass a method as a parameter to another method, or to store a reference to a method for later execution. Delegates are often used as event handlers in C#, since they provide a convenient way to define the signature of the method that will handle the event.

The main difference between an event and a delegate is that an event is a higher-level concept that encapsulates a delegate. While a delegate is simply a reference to a method, an event provides a way to subscribe to and unsubscribe from the events raised by an object. When an event is raised, all of the event handlers that have subscribed to the event are notified and called in the order in which they were added.

In summary, while a delegate is a reference to a method, an event is a higher-level concept that uses a delegate to notify other objects when something happens.