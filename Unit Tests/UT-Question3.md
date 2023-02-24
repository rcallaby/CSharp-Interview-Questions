# Question 3 - Unit Tests

## How do you use the xUnit framework to write and run unit tests in C#?

xUnit is a popular testing framework for .NET and C#. To use xUnit to write and run unit tests in C#, follow these steps:

Install xUnit: First, you need to install the xUnit NuGet package in your project. You can do this by opening the NuGet package manager console and running the following command:

```
Install-Package xunit

```
Create a test project: In Visual Studio, create a new project and select the "xUnit Test Project" template under the "Test" category.

Write a test: In the test project, create a new class and add a test method to it. A test method is a public method that is annotated with the [Fact] attribute. Here is an example of a test method:

```
public class MyTests
{
    [Fact]
    public void TestAddition()
    {
        // Arrange
        int a = 2;
        int b = 3;
        int expected = 5;

        // Act
        int actual = a + b;

        // Assert
        Assert.Equal(expected, actual);
    }
}

```
In this example, the TestAddition method tests the addition of two numbers. The Assert.Equal method checks if the actual result of the addition is equal to the expected result.

Run the test: To run the test, open the Test Explorer window in Visual Studio by going to Test > Windows > Test Explorer. You should see your test method listed there. Click the "Run All" button to run all the tests in the test project.
That's it! You can now use xUnit to write and run unit tests in your C# projects. You can add more test methods to your test class to test different parts of your code. You can also use other xUnit attributes, such as [Theory] to write parameterized tests, or [SetUp] and [TearDown] to set up and tear down test fixtures.