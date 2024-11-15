# Question 12 - Inheritance

## Can you give an example of how to use the is operator and the as operator with inheritance in C#?

Let's say we have a class hierarchy as follows:

```csharp
class Animal
{
    public virtual void MakeSound()
    {
        Console.WriteLine("Animal sound");
    }
}

class Cat : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Meow");
    }
}

class Dog : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Woof");
    }
}

```
Now, we can use the is operator to check if an object is an instance of a particular class or one of its derived classes. For example:

```csharp
Animal animal = new Cat();

if (animal is Cat)
{
    Cat cat = (Cat)animal;
    cat.Purr();
}

```
In the above code, we create an instance of Cat and assign it to an Animal variable. We then use the is operator to check if the object referred to by animal is a Cat. If it is, we cast it to a Cat and call the Purr method (which we assume is defined in the Cat class).

We can also use the as operator to perform a safe cast to a derived class. If the object is not an instance of the derived class, the result will be null. For example:

```csharp
Animal animal = new Dog();

Cat cat = animal as Cat;

if (cat != null)
{
    cat.Purr();
}
else
{
    Console.WriteLine("Not a cat");
}

```
In the above code, we create an instance of Dog and assign it to an Animal variable. We then use the as operator to cast it to a Cat. Since the object is not a Cat, the result of the cast will be null, so we check for that and print a message if it is null. If the cast had succeeded, we could have called the Purr method on the cat variable.