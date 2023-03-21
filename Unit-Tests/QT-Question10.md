# Question 10 - Unit Tests

## Can you give an example of how to use dependency injection to make code more testable in C#?

Let's say you have a class called OrderProcessor that depends on a PaymentProcessor to process payments. Here's how the OrderProcessor class might look like without dependency injection:

```
public class OrderProcessor
{
    private readonly PaymentProcessor _paymentProcessor;
    
    public OrderProcessor()
    {
        _paymentProcessor = new PaymentProcessor();
    }

    public void ProcessOrder(Order order)
    {
        // Do some order processing logic

        _paymentProcessor.ProcessPayment(order);

        // Do some more order processing logic
    }
}

```
The problem with this code is that the OrderProcessor class has a hard dependency on the PaymentProcessor class. This makes it difficult to test the ProcessOrder method in isolation because you cannot easily replace the PaymentProcessor with a test double.

Here's how you could refactor the OrderProcessor class to use dependency injection instead:

```
public class OrderProcessor
{
    private readonly IPaymentProcessor _paymentProcessor;
    
    public OrderProcessor(IPaymentProcessor paymentProcessor)
    {
        _paymentProcessor = paymentProcessor;
    }

    public void ProcessOrder(Order order)
    {
        // Do some order processing logic

        _paymentProcessor.ProcessPayment(order);

        // Do some more order processing logic
    }
}

```
In this version of the OrderProcessor class, the PaymentProcessor dependency has been abstracted away behind an interface called IPaymentProcessor. The OrderProcessor class now takes an IPaymentProcessor instance as a constructor parameter, which can be provided by a dependency injection container.

Here's an example of how you could use a dependency injection container like Microsoft.Extensions.DependencyInjection to register the IPaymentProcessor implementation and inject it into the OrderProcessor class:

```
var services = new ServiceCollection();
services.AddSingleton<IPaymentProcessor, PaymentProcessor>();
services.AddTransient<OrderProcessor>();
var serviceProvider = services.BuildServiceProvider();

var orderProcessor = serviceProvider.GetService<OrderProcessor>();

```
Now you can easily create a test double of the IPaymentProcessor interface and inject it into the OrderProcessor class for testing purposes. This makes it much easier to test the ProcessOrder method in isolation.