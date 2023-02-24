# Question 15 - Inheritance

## What is the difference between inheritance and composition in C# and when should you use each one?

Inheritance and composition are two fundamental concepts in object-oriented programming that allow developers to build more complex and robust software systems.

Inheritance is a mechanism that allows a class to inherit the characteristics of another class, referred to as the base or parent class. In C#, this is achieved using the "extends" keyword. The derived or child class inherits all the non-private members (methods, properties, and fields) of the parent class and can also add new members or override existing ones. Inheritance is often used to model an "is-a" relationship between classes, where a derived class represents a more specialized version of the parent class.

Composition, on the other hand, is a mechanism that allows a class to contain objects of other classes, referred to as its components. In C#, this is achieved by creating a field in the class that holds a reference to an instance of another class. Composition is often used to model a "has-a" relationship between classes, where a class has one or more components that are essential to its functionality.

So, when should you use inheritance vs composition? Here are some guidelines:

Use inheritance when you want to model an "is-a" relationship between classes, where a derived class is a more specialized version of the parent class. For example, a Dog class may inherit from an Animal class because a dog is a type of animal.

Use composition when you want to model a "has-a" relationship between classes, where a class has one or more components that are essential to its functionality. For example, a Car class may have a Engine component because a car needs an engine to function.

In general, prefer composition over inheritance, because it leads to more flexible and maintainable code. With composition, you can easily change the behavior of a class by replacing one of its components, whereas with inheritance, you are more tightly coupled to the parent class's implementation.

Avoid deep inheritance hierarchies, as they can make the code difficult to understand and maintain. Instead, use interfaces to define common behaviors that classes can implement.