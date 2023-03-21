# Question 7 - Abstract Classes

## Can you explain the SOLID principle of Liskov Substitution and how it relates to abstract classes in C#?

The Liskov Substitution Principle (LSP) is a fundamental principle of object-oriented programming that states that objects of a superclass should be able to be replaced with objects of its subclasses without affecting the correctness of the program. In other words, if a program is designed to work with a superclass object, it should also work with any of its subclasses.

In C#, abstract classes are often used to implement Liskov Substitution. Abstract classes are classes that cannot be instantiated, but instead serve as a template for other classes to inherit from. When a class inherits from an abstract class, it must provide implementations for all of the abstract methods declared in the abstract class. This ensures that any object created from the subclass can be substituted for an object of the superclass, without affecting the correctness of the program.

For example, consider a program that uses a superclass called "Animal" to represent different types of animals, with a method called "MakeSound" that all animals should implement. We can use an abstract class to define the Animal class and make the MakeSound method abstract, like so:

```
public abstract class Animal
{
    public abstract void MakeSound();
}

```
Then, we can create subclasses for different types of animals, like "Cat", "Dog", and "Bird", that inherit from the Animal class and implement the MakeSound method:

```
public class Cat : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Meow");
    }
}

public class Dog : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Woof");
    }
}

public class Bird : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Chirp");
    }
}

```
Now, we can create objects of the different animal types and use them interchangeably, because they all inherit from the same Animal superclass and implement the same MakeSound method:

```
Animal cat = new Cat();
Animal dog = new Dog();
Animal bird = new Bird();

cat.MakeSound(); // prints "Meow"
dog.MakeSound(); // prints "Woof"
bird.MakeSound(); // prints "Chirp"

```
This demonstrates the Liskov Substitution Principle, because we can use objects of the subclass types (Cat, Dog, Bird) in place of the superclass type (Animal), without affecting the correctness of the program.