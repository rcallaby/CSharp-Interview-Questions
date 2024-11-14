# Question 2 - Inheritance

## Can you give an example of inheritance in C#?

In C#, inheritance allows you to define a new class based on an existing class. The new class will inherit all the members of the existing class (fields, properties, methods, etc.) and can also add its own members.

Here is an example of inheritance in C#:

```csharp
// base class
public class Animal
{
    public string Name { get; set; }
    public int Age { get; set; }
    
    public void Eat()
    {
        Console.WriteLine("The animal is eating.");
    }
}

// derived class
public class Cat : Animal
{
    public void Meow()
    {
        Console.WriteLine("The cat is meowing.");
    }
}

// usage
Cat cat = new Cat();
cat.Name = "Fluffy";
cat.Age = 3;
cat.Eat(); // output: "The animal is eating."
cat.Meow(); // output: "The cat is meowing."

```
In this example, the Cat class is a derived class of the Animal class. The Cat class inherits the Name and Age properties, as well as the Eat() method from the Animal class. It also has its own Meow() method that is specific to cats.

When an instance of the Cat class is created, it can access both the inherited members from the Animal class and its own members, as shown in the usage section.
