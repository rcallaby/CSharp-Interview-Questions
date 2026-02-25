# Question 6 - Abstract Classes

## How can abstract classes be used to implement the Dependency Inversion principle?

The Dependency Inversion principle (DIP) states that high-level modules should not depend on low-level modules, but rather both should depend on abstractions. Abstractions should not depend on details, but details should depend on abstractions.

In C#, one way to implement DIP using abstract classes is by defining an abstract class that represents the abstraction, and then defining concrete implementations of that abstraction in lower-level modules.

Here is an example of how this can be done:

```
public abstract class ILogger
{
    public abstract void Log(string message);
}

public class FileLogger : ILogger
{
    public void Log(string message)
    {
        // Log message to a file
    }
}

public class DatabaseLogger : ILogger
{
    public void Log(string message)
    {
        // Log message to a database
    }
}

public class Application
{
    private readonly ILogger _logger;

    public Application(ILogger logger)
    {
        _logger = logger;
    }

    public void DoSomething()
    {
        // Do something

        _logger.Log("Did something");
    }
}

```
In this example, ILogger is an abstract class that represents the abstraction of a logger. FileLogger and DatabaseLogger are concrete implementations of the ILogger abstraction in lower-level modules.

The Application class is a higher-level module that depends on the ILogger abstraction. Instead of depending on a specific implementation of ILogger, Application depends on the abstraction itself. This allows different implementations of ILogger to be used without changing the Application class.

By using abstract classes to define abstractions and depending on those abstractions instead of concrete implementations, we can achieve the Dependency Inversion principle in our code.