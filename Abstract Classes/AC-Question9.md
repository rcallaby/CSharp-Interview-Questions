# Question 9 - Abstract Classes

## Can you give an example of how abstract classes can help to enforce the Interface Segregation principle?

Let's say we have an interface called IAnimal that has several methods related to animal behavior, such as Eat(), Sleep(), and Move(). However, not all animals have the same behavior, so it might be difficult to create a single interface that covers all animal types.

One way to enforce the Interface Segregation principle in this scenario is to create abstract classes that implement subsets of the methods in the IAnimal interface. For example:

```
public interface IAnimal {
    void Eat();
    void Sleep();
    void Move();
}

public abstract class Carnivore : IAnimal {
    public void Eat() {
        // Carnivores have a specific way of eating
    }

    public void Sleep() {
        // All animals sleep similarly
    }

    public abstract void Move();
}

public abstract class Herbivore : IAnimal {
    public void Eat() {
        // Herbivores have a specific way of eating
    }

    public void Sleep() {
        // All animals sleep similarly
    }

    public abstract void Move();
}

```
In this example, we've created two abstract classes Carnivore and Herbivore that implement the Eat() and Sleep() methods from the IAnimal interface. These abstract classes also declare an abstract Move() method, which allows subclasses to implement their own version of Move() depending on the specific animal type.

By creating these abstract classes, we've separated the methods in the IAnimal interface into smaller, more specific groups of behavior. This helps ensure that classes that implement IAnimal only need to implement the methods that are relevant to their specific behavior, rather than having to implement all the methods in the interface, which might not be necessary or applicable for all animal types.