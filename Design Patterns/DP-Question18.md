# Question 18 - Design Patterns

## How can you use the Mediator pattern in C# to reduce coupling between objects?

The Mediator pattern is a behavioral design pattern that is used to reduce coupling between objects by introducing a mediator object that acts as an intermediary between the objects to handle all their communication. In this pattern, the objects no longer communicate directly with each other, but instead communicate with the mediator, which then communicates with the other objects. This reduces the dependencies between the objects, making the system more flexible and scalable.

Here's an example of how you can implement the Mediator pattern in C#:

```
public interface IMediator
{
    void SendMessage(string message, Colleague colleague);
}

public abstract class Colleague
{
    protected IMediator mediator;

    public Colleague(IMediator mediator)
    {
        this.mediator = mediator;
    }
}

public class ConcreteColleagueA : Colleague
{
    public ConcreteColleagueA(IMediator mediator) : base(mediator) { }

    public void Send(string message)
    {
        mediator.SendMessage(message, this);
    }

    public void Notify(string message)
    {
        Console.WriteLine("ColleagueA receives message: " + message);
    }
}

public class ConcreteColleagueB : Colleague
{
    public ConcreteColleagueB(IMediator mediator) : base(mediator) { }

    public void Send(string message)
    {
        mediator.SendMessage(message, this);
    }

    public void Notify(string message)
    {
        Console.WriteLine("ColleagueB receives message: " + message);
    }
}

public class ConcreteMediator : IMediator
{
    private ConcreteColleagueA colleagueA;
    private ConcreteColleagueB colleagueB;

    public ConcreteColleagueA ColleagueA
    {
        set { colleagueA = value; }
    }

    public ConcreteColleagueB ColleagueB
    {
        set { colleagueB = value; }
    }

    public void SendMessage(string message, Colleague colleague)
    {
        if (colleague == colleagueA)
        {
            colleagueB.Notify(message);
        }
        else
        {
            colleagueA.Notify(message);
        }
    }
}

```
In this example, the IMediator interface defines the methods that the mediator object must implement, and the Colleague class is an abstract class that represents the objects that communicate with each other. The concrete ConcreteColleagueA and ConcreteColleagueB classes represent specific objects that communicate with each other through the mediator. Finally, the ConcreteMediator class implements the IMediator interface and acts as the intermediary between the objects.
