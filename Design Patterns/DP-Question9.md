# Question 9 - Design Patterns

## What is the Prototype pattern in C# and how does it differ from the Factory Method pattern?

The Prototype pattern is a creational design pattern that enables you to create a new object by copying an existing object. The existing object acts as a prototype for the new object, and the new object is typically an exact copy of the prototype. This pattern can be used to reduce the number of classes you need to create, and it also makes it easier to create new objects since you can simply copy an existing object, rather than having to create a new object from scratch.

In C#, you can implement the Prototype pattern by defining an interface (or abstract class) that contains a Clone method. The Clone method is used to create a new object that is a copy of the original object. You can then implement this interface (or abstract class) in your concrete classes, providing an implementation for the Clone method that creates a copy of the object.

The Factory Method pattern, on the other hand, is a creational design pattern that provides a way to create objects without having to specify the exact class of the object that will be created. In this pattern, a factory method is used to create an object, and the factory method is defined in a separate class called a factory. The factory class is responsible for deciding which class to instantiate, and it returns an instance of that class.

In C#, you can implement the Factory Method pattern by defining an abstract factory class that contains a factory method. The factory method is used to create an object, and it is implemented by concrete factory classes. Each concrete factory class provides an implementation of the factory method that creates an instance of a specific type of object.

The main difference between the Prototype and Factory Method patterns is that the Prototype pattern focuses on copying existing objects, while the Factory Method pattern focuses on creating new objects based on a factory method. The Prototype pattern is typically used when you need to create a new object that is a copy of an existing object, while the Factory Method pattern is typically used when you need to create a new object but you don't want to specify the exact class of the object that will be created.