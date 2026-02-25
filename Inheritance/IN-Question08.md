# Question 8 - Inheritance

## Can you give an example of how to use inheritance to create a hierarchy of classes in C#?

Here's an example of how to use inheritance to create a hierarchy of classes in C#:

```
// Define a base class
public class Animal
{
    public string Name { get; set; }
    public int Age { get; set; }

    public void Eat()
    {
        Console.WriteLine("The animal is eating.");
    }
}

// Define a derived class
public class Dog : Animal
{
    public void Bark()
    {
        Console.WriteLine("The dog is barking.");
    }
}

// Define another derived class
public class Cat : Animal
{
    public void Meow()
    {
        Console.WriteLine("The cat is meowing.");
    }
}

```
In this example, we define a base class Animal with a Name and Age property, as well as an Eat method. We then define two derived classes, Dog and Cat, which inherit from the Animal base class.

The Dog class adds a Bark method, while the Cat class adds a Meow method. Both derived classes inherit the Name, Age, and Eat members from the Animal base class.

With this hierarchy of classes, we can create instances of Dog and Cat and call their respective methods:

```
Dog myDog = new Dog();
myDog.Name = "Fido";
myDog.Age = 3;
myDog.Bark(); // Output: "The dog is barking."
myDog.Eat(); // Output: "The animal is eating."

Cat myCat = new Cat();
myCat.Name = "Fluffy";
myCat.Age = 2;
myCat.Meow(); // Output: "The cat is meowing."
myCat.Eat(); // Output: "The animal is eating."

```
Note that since Dog and Cat inherit from Animal, we can use variables of type Animal to refer to instances of Dog and Cat, and call the Eat method on them:

```
Animal myAnimal = new Dog();
myAnimal.Eat(); // Output: "The animal is eating."

```
