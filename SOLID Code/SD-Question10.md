# Question 10 - SOLID

## Can you describe the difference between Structural and Behavioral design patterns in C#, and provide an example of each?

Structural design patterns are concerned with the composition of classes and objects to form larger structures, such as interfaces, inheritance, and composition. They help to simplify the relationships between objects by identifying common communication patterns and providing a way to ensure that objects work together effectively.

One example of a structural design pattern in C# is the Adapter pattern, which is used to adapt one interface to another. This pattern allows objects with incompatible interfaces to work together by creating a new class that acts as a bridge between them. An example of this pattern in action would be a class that adapts a legacy API to a modern interface.

Behavioral design patterns, on the other hand, are focused on the interaction between objects and how they communicate with each other. These patterns help to identify common patterns of communication between objects, and provide a way to manage these interactions in a more efficient and effective manner.

An example of a behavioral design pattern in C# is the Command pattern, which is used to encapsulate a request as an object, allowing it to be passed around and executed later. This pattern decouples the requester of a request from the object that performs the request, allowing for greater flexibility in the system. An example of this pattern in action would be a text editor that uses a command object to represent various operations, such as cut, copy, and paste.