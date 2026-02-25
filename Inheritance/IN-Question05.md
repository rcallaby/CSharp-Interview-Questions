# Question 5 - Inheritance

## Can you explain the concept of polymorphism and how it relates to inheritance in C#?

Polymorphism is a concept in object-oriented programming that refers to the ability of objects of different types to be treated as if they are of the same type. This allows for greater flexibility in the use of code, as it can be written to accept multiple types of objects without needing to know their specific implementation details.

In C#, polymorphism is closely related to inheritance. Inheritance is a way of creating new classes by deriving them from existing classes, with the new classes inheriting the properties and methods of the base classes. Polymorphism takes advantage of this relationship by allowing objects of derived classes to be used in place of objects of their base classes.

For example, let's say we have a base class called "Animal" with a method called "MakeSound". We also have two derived classes called "Dog" and "Cat", which override the "MakeSound" method with their own unique implementations. If we create objects of the "Dog" and "Cat" classes, we can treat them as if they are objects of the "Animal" class and call the "MakeSound" method on them, which will result in the appropriate implementation being called based on their specific type.

This is achieved through the use of virtual and override keywords in C#. The base class can declare a method as virtual, which means it can be overridden by derived classes. The derived classes can then use the override keyword to provide their own implementation of the method. When an object of a derived class is used in place of an object of the base class, the appropriate implementation of the overridden method will be called based on the object's actual type. This is known as dynamic binding, as the method implementation is determined at runtime based on the type of the object.