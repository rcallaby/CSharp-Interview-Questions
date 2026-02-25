# Question 9 - LINQ

## Can you give an example of using LINQ to implement the Interface Segregation Principle (ISP)?

Suppose we have an interface called IAnimal that represents different types of animals. Some animals can swim, some can fly, and some can walk. Here's what the interface might look like:

```
public interface IAnimal
{
    void Swim();
    void Fly();
    void Walk();
}

```
However, this interface violates the ISP because it has too many methods and not all animals can perform all actions. To fix this, we can break up the IAnimal interface into smaller, more focused interfaces.

For example, we can create an ISwimmable interface for animals that can swim:

```
public interface ISwimmable
{
    void Swim();
}

```
We can also create an IFlyable interface for animals that can fly:

```
public interface IFlyable
{
    void Fly();
}

```
And finally, we can create an IWalkable interface for animals that can walk:

```
public interface IWalkable
{
    void Walk();
}

```
Now we can implement these interfaces in our animal classes as needed. For example, a Dolphin class would implement ISwimmable:

```
public class Dolphin : ISwimmable
{
    public void Swim()
    {
        Console.WriteLine("The dolphin is swimming.");
    }
}

```
And a Bird class would implement IFlyable:

```
public class Bird : IFlyable
{
    public void Fly()
    {
        Console.WriteLine("The bird is flying.");
    }
}

```
We can use LINQ to query collections of animals based on their capabilities. For example, to find all the animals that can swim, we can use the following LINQ query:

```
var swimmableAnimals = animals.OfType<ISwimmable>();
```

This query uses the OfType method to filter the animals collection to only those that implement the ISwimmable interface. Similarly, we can find all the animals that can fly with the following query:

```
var flyableAnimals = animals.OfType<IFlyable>();

```

And all the animals that can walk with this query:

```
var walkableAnimals = animals.OfType<IWalkable>();
```
By breaking up the IAnimal interface into smaller interfaces, we've adhered to the ISP and made our code more modular and flexible. Using LINQ to query collections of animals based on their capabilities allows us to write more concise and expressive code.

