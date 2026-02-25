# Question 5 - Design Patterns

# Can you please tell me what is the Observer Pattern in C# and how does it work?

The Observer Pattern is a design pattern in software engineering that defines a one-to-many dependency between objects so that when one object changes state, all of its dependents are notified and updated automatically. In C#, it can be implemented using events and delegates.

Here's how it works:

The subject, also known as the publisher, maintains a list of its dependents, known as observers, and provides an interface to add or remove observers.

Observers subscribe to the subject by registering themselves to receive notifications.

When the state of the subject changes, it sends a notification to all its observers.

Observers receive the notification and update themselves accordingly.

Here's an example implementation in C#:

```
public class Subject
{
    private List<Observer> _observers = new List<Observer>();
    private int _state;

    public int State
    {
        get { return _state; }
        set
        {
            _state = value;
            Notify();
        }
    }

    public void Attach(Observer observer)
    {
        _observers.Add(observer);
    }

    public void Detach(Observer observer)
    {
        _observers.Remove(observer);
    }

    private void Notify()
    {
        foreach (var observer in _observers)
        {
            observer.Update(this);
        }
    }
}

public class Observer
{
    public void Update(Subject subject)
    {
        Console.WriteLine("Subject state updated to: " + subject.State);
    }
}

```
In this example, the Subject class maintains a list of Observer objects, and the Observer class has an Update method that is called whenever the state of the subject changes. Observers can subscribe to the subject by calling the Attach method, and they can unsubscribe by calling the Detach method.


