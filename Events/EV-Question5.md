# Question 5 - Events

## Can you explain the difference between an event and a delegate in C#?

In C#, an event and a delegate are related concepts, but they serve different purposes.

An event is a mechanism in C# that enables an object to notify other objects when something of interest occurs. An event is essentially a set of delegates (or a delegate chain) that get called when the event is raised. Events can only be raised by the class that defines them or a derived class, and they can only be subscribed to by other classes.

A delegate, on the other hand, is a type that represents a reference to a method with a specific signature. A delegate can be thought of as a type-safe function pointer. Delegates can be used to pass methods as arguments to other methods or to store references to methods in a collection.

In the context of events, a delegate is used to define the signature of the methods that can be subscribed to an event. When an event is raised, the delegate is called, and all the methods that have been subscribed to the event are executed.

In summary, an event is a mechanism for allowing an object to notify other objects when something of interest occurs, while a delegate is a type that represents a reference to a method with a specific signature. An event uses a delegate to call the methods that have been subscribed to it.