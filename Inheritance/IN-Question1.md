# Question 1 - Inheritance

## What is inheritance in C# and how does it work?

Inheritance in C# is a mechanism that allows a class to inherit properties and behavior from another class, which is called the base or parent class. The class that inherits from the parent class is called the derived or child class.

To create an inheritance relationship between two classes in C#, the derived class includes a colon (:) and the name of the parent class in its declaration, as shown in the following syntax:

```
class DerivedClass : ParentClass
{
    // class members
}

```
The derived class then automatically inherits all the members of the parent class, including fields, properties, methods, and events. The derived class can also add its own members or override the inherited members.

For example, consider the following code:

```
class Animal
{
    public string Name { get; set; }
    
    public void MakeSound()
    {
        Console.WriteLine("Animal makes a sound.");
    }
}

class Dog : Animal
{
    public void WagTail()
    {
        Console.WriteLine("Dog wags its tail.");
    }
    
    public override void MakeSound()
    {
        Console.WriteLine("Dog barks.");
    }
}

```
In this example, the Dog class inherits from the Animal class, which has a Name property and a MakeSound() method. The Dog class adds a WagTail() method and overrides the MakeSound() method to make the dog bark instead of just making a generic animal sound.

Now, we can create an instance of the Dog class and use its inherited and new members:

```
Dog myDog = new Dog();
myDog.Name = "Buddy";
myDog.MakeSound(); // Output: "Dog barks."
myDog.WagTail(); // Output: "Dog wags its tail."

```
In this example, the myDog object has access to the Name property inherited from the Animal class, as well as the MakeSound() method that was overridden by the Dog class. It also has access to the new WagTail() method added by the Dog class.
