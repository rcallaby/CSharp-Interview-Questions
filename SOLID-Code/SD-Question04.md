# Question 4 - SOLID

## Can you describe the difference between Inheritance and Composition in C#, and how you would choose between them for a given scenario?

Inheritance and Composition are two fundamental concepts in Object-Oriented Programming (OOP) that allow programmers to create relationships between classes in C#.

Inheritance refers to a mechanism in which a new class is created by inheriting the properties and methods of an existing class, known as the base or parent class. The new class, known as the derived or child class, can then add or modify the behavior of the parent class through the use of methods and properties. Inheritance creates an "is-a" relationship between classes, where the derived class is a type of the parent class.

Composition, on the other hand, refers to a mechanism in which a class is composed of one or more instances of other classes. The composed classes, known as components, are used to provide the functionality of the containing class. Composition creates a "has-a" relationship between classes, where the containing class has one or more components that it uses to provide its functionality.

When choosing between inheritance and composition for a given scenario, it is important to consider the nature of the relationship between the classes. In general, inheritance should be used when there is a clear "is-a" relationship between the classes, where the derived class can be seen as a specialized version of the parent class. For example, a Dog class can inherit from an Animal class, because a dog is a type of animal.

On the other hand, composition should be used when there is a "has-a" relationship between the classes, where the containing class uses one or more components to provide its functionality. For example, a Car class can be composed of instances of an Engine class, a Transmission class, and a Chassis class, because a car has an engine, a transmission, and a chassis.

In general, it is a good practice to favor composition over inheritance whenever possible, as it leads to more flexible and maintainable code. Composition allows classes to be easily composed of multiple components, which can be swapped in and out as needed, without affecting the functionality of the containing class. In contrast, inheritance can lead to tightly-coupled and brittle code, as changes to the base class can have unexpected effects on the derived classes.