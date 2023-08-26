# Question 2 - General Questions

## What is object-oriented programming?

Object-Oriented Programming (OOP) is a programming paradigm that focuses on organizing code into objects, which are instances of classes. It promotes the idea of encapsulating data (attributes) and behavior (methods) related to a specific entity into a single unit. C# is a language that fully supports OOP concepts.

In C#, classes serve as blueprints for creating objects. Let's go through some OOP concepts in C# with examples:

Class and Object Creation:
A class is a template that defines the structure and behavior of objects. An object is an instance of a class.

```
class Person
{
    public string Name;
    public int Age;

    public void Introduce()
    {
        Console.WriteLine($"Hi, I'm {Name} and I'm {Age} years old.");
    }
}

class Program
{
    static void Main()
    {
        Person person1 = new Person();
        person1.Name = "Alice";
        person1.Age = 30;
        person1.Introduce(); // Output: Hi, I'm Alice and I'm 30 years old.
    }
}


```
Encapsulation:
Encapsulation ensures that the internal details of an object are hidden from the outside world. It helps maintain data integrity and allows controlled access to data through methods.

```
class BankAccount
{
    private double balance;

    public void Deposit(double amount)
    {
        if (amount > 0)
            balance += amount;
    }

    public void Withdraw(double amount)
    {
        if (amount > 0 && amount <= balance)
            balance -= amount;
    }

    public double GetBalance()
    {
        return balance;
    }
}


```
Inheritance:
Inheritance allows you to create a new class based on an existing class, inheriting its attributes and methods. It promotes code reusability and hierarchy.

```
class Animal
{
    public string Species;

    public void MakeSound()
    {
        Console.WriteLine("Animal makes a sound.");
    }
}

class Dog : Animal
{
    public void Bark()
    {
        Console.WriteLine("Woof woof!");
    }
}


```
Polymorphism:
Polymorphism allows objects of different classes to be treated as objects of a common base class through inheritance. It enables dynamic method binding and flexibility in handling different object types.

```
class Shape
{
    public virtual void Draw()
    {
        Console.WriteLine("Drawing a shape.");
    }
}

class Circle : Shape
{
    public override void Draw()
    {
        Console.WriteLine("Drawing a circle.");
    }
}

class Square : Shape
{
    public override void Draw()
    {
        Console.WriteLine("Drawing a square.");
    }
}


```
These are just a few fundamental concepts of Object-Oriented Programming in C#. They provide a way to structure your code, improve reusability, and create more maintainable software applications.