# Question 11 - Design Patterns

## What is the adaptor pattern in C# and how is it used to integrate with existing systems?

The adapter pattern is a software design pattern that allows two incompatible interfaces to work together by creating a bridge between them. It is used to help integrate existing systems by converting the interface of one class into an interface that another class expects.

In C#, the adapter pattern can be implemented by creating a class that implements the target interface and holds a reference to an instance of the adaptee class. The adapter class then delegates all calls from the target interface to the adaptee, converting the request into the form expected by the adaptee.

For example, consider an existing system that provides an API for processing payments through a class named "PaymentProcessor". If you need to integrate this system with a new application that expects a different payment processing API, you could create an adapter class named "PaymentProcessorAdapter" that implements the new API and delegates calls to the "PaymentProcessor" class.

Here's a simple example in C#:

```
public interface IPaymentProcessor
{
    void ProcessPayment(decimal amount);
}

public class PaymentProcessor
{
    public void ProcessPayment(string customerId, decimal amount)
    {
        // Perform payment processing
    }
}

public class PaymentProcessorAdapter : IPaymentProcessor
{
    private readonly PaymentProcessor _paymentProcessor;

    public PaymentProcessorAdapter(PaymentProcessor paymentProcessor)
    {
        _paymentProcessor = paymentProcessor;
    }

    public void ProcessPayment(decimal amount)
    {
        _paymentProcessor.ProcessPayment("12345", amount);
    }
}

```
In this example, the "PaymentProcessorAdapter" class implements the "IPaymentProcessor" interface and acts as an adapter between the "PaymentProcessor" class and the new application that expects a different payment processing API. When the new application calls the ProcessPayment method, the adapter delegates the call to the ProcessPayment method of the PaymentProcessor class, passing in the required parameters.
