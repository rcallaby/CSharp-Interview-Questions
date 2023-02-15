# Question 4 - General Questions

## Can you explain polymorphism and how it is achieved in C#?

Polymorphism is a concept in object-oriented programming (OOP) that allows objects of different types to be treated as if they were the same type, providing a way to write code that is more flexible and reusable.

In C#, polymorphism can be achieved in several ways, including:

Method Overloading: This allows you to define multiple methods with the same name, but with different parameters. C# will determine which method to call based on the number and types of the arguments passed to it.

Method Overriding: This allows a subclass to provide a different implementation of a method that is already defined in its superclass. When the method is called on an instance of the subclass, the overridden version is executed instead of the superclass version.

Interfaces: An interface is a contract that specifies a set of methods and properties that a class must implement. This allows objects of different types to be treated as if they were of the same type as long as they implement the same interface.

Here's an example that shows how polymorphism can be achieved using method overriding in C#:

```
public class Animal {
    public virtual void MakeSound() {
        Console.WriteLine("Animal makes a sound.");
    }
}

public class Cat : Animal {
    public override void MakeSound() {
        Console.WriteLine("Meow.");
    }
}

public class Dog : Animal {
    public override void MakeSound() {
        Console.WriteLine("Woof.");
    }
}

// Usage
Animal animal1 = new Cat();
animal1.MakeSound(); // outputs "Meow."

Animal animal2 = new Dog();
animal2.MakeSound(); // outputs "Woof."

```
In this example, we have a base class Animal with a virtual MakeSound() method. The Cat and Dog classes inherit from Animal and override the MakeSound() method with their own implementation. We can then create instances of Cat and Dog, but store them in variables of type Animal. When we call the MakeSound() method on these variables, the overridden version of the method in the corresponding subclass is executed.