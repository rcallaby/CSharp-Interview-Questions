# Question 4 - Unit Tests

## Can you explain how to write a test case for checking the exception handling in C#?

Here's an example of how to write a test case for checking the exception handling in C# using the NUnit testing framework:

```
using NUnit.Framework;

[TestFixture]
public class ExceptionHandlingTests
{
    [Test]
    public void TestDivideByZeroException()
    {
        // Arrange
        int numerator = 10;
        int denominator = 0;

        // Act and Assert
        Assert.Throws<DivideByZeroException>(() => DivideNumbers(numerator, denominator));
    }

    private int DivideNumbers(int numerator, int denominator)
    {
        if (denominator == 0)
        {
            throw new DivideByZeroException("Denominator cannot be zero.");
        }

        return numerator / denominator;
    }
}

```
In this example, we have a test method called TestDivideByZeroException that tests if the DivideNumbers method throws a DivideByZeroException when the denominator is zero.

The Assert.Throws method expects an exception to be thrown of a specific type, in this case DivideByZeroException. The method takes a lambda expression that represents the code being tested. If the code being tested does not throw an exception of the expected type, the test will fail.

Note that it's important to use a try-catch block when testing exception handling to ensure that any exceptions that are not expected are caught and handled properly, and that the test is not considered a false positive.