# Question 9 - Inheritance

## What is an interface in C# and how is it related to inheritance?

In C#, an interface is a programming construct that defines a set of abstract methods, properties, events, and indexers that a class can implement. An interface specifies the members that a class must provide, but it does not provide the implementation of those members.

An interface is related to inheritance in that a class can implement one or more interfaces, and the class that implements an interface must provide an implementation for all the members specified by the interface. In other words, the interface defines a contract that the implementing class must follow.

When a class implements an interface, it must provide implementations for all the members specified by the interface. This means that the class must provide its own implementation of the abstract methods, properties, events, and indexers defined by the interface.

By implementing an interface, a class can provide a specific set of functionality to other classes, without the need for those classes to know the implementation details of the implementing class. This allows for greater flexibility and modularity in the design of software systems, as classes can be designed to work with each other based on the interfaces they implement, rather than on their concrete implementation details.

Inheritance is also related to interfaces in that a class can inherit from a base class and also implement one or more interfaces. This allows the class to both reuse the implementation of the base class and provide additional functionality specified by the interface.