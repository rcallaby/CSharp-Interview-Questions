# Question 7 - Design Patterns

## What is the Command Pattern in C# and how is it used?

The Command Pattern is a behavioral design pattern that turns a request into a stand-alone object that contains all information about the request. This transformation lets you pass requests as a method arguments, delay or queue a request’s execution, and implement deferred execution of operations.

In C#, the Command pattern is implemented by creating classes that represent each command and encapsulate all the information required to perform the specific action. These classes typically implement an interface, such as ICommand, which defines a single Execute method. The client code creates concrete command objects and sets their receiver using the appropriate properties or constructor arguments.

Here is a simple example of how the Command pattern can be used in C# to implement undo-redo functionality:

```
interface ICommand
{
    void Execute();
    void Undo();
}

class AddCommand : ICommand
{
    private readonly int _value;
    private readonly Calculator _calculator;

    public AddCommand(Calculator calculator, int value)
    {
        _calculator = calculator;
        _value = value;
    }

    public void Execute()
    {
        _calculator.Add(_value);
    }

    public void Undo()
    {
        _calculator.Subtract(_value);
    }
}

class Calculator
{
    private int _currentValue;

    public void Add(int value)
    {
        _currentValue += value;
    }

    public void Subtract(int value)
    {
        _currentValue -= value;
    }
}

```
In this example, the AddCommand class implements the ICommand interface and contains all the information required to add a value to a calculator. The Execute method performs the addition, while the Undo method performs the reverse operation, subtraction. The client code can create instances of the AddCommand class and use them to perform additions and undo them later.