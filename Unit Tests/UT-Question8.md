# Question 8 - Unit Tests

## Can you describe the process of test-driven development (TDD) and how it can be applied to C# development?

Test-driven development (TDD) is a software development process in which tests are written before the code is implemented. This process is iterative and requires developers to write a failing test, write code to make the test pass, and then refactor the code to improve its design and maintainability. Here's a brief overview of the TDD process:

Write a failing test: In TDD, you start by writing a test that will fail because the functionality you're testing hasn't been implemented yet. The test should be as specific as possible and should define what the code should do.

Write the code: After you have written the failing test, you write the minimum amount of code required to make the test pass. The code you write should be as simple as possible and should only implement the functionality required to pass the test.

Run the test: Once you have written the code, you run the test to ensure that it passes. If the test fails, you go back and modify the code until the test passes.

Refactor the code: After the test has passed, you can refactor the code to improve its design and maintainability. You should only refactor the code if all the tests pass.

Repeat the process: You then repeat the process with another test until all the required functionality has been implemented.

In C# development, TDD can be applied using testing frameworks such as NUnit, MSTest, or xUnit. Here's an example of how TDD can be applied to C# development:

Write a failing test: In this step, you would write a test that will fail because the functionality you're testing hasn't been implemented yet. For example, if you're building a calculator, you might write a test that asserts that adding two numbers returns the correct result.

```
[Test]
public void TestAddition()
{
    Calculator calculator = new Calculator();
    int result = calculator.Add(2, 3);
    Assert.AreEqual(5, result);
}

```
Write the code: In this step, you write the minimum amount of code required to make the test pass. For example, you might implement the Add method of the Calculator class:

```
public class Calculator
{
    public int Add(int x, int y)
    {
        return x + y;
    }
}

```
Run the test: Once you have written the code, you run the test to ensure that it passes.

Refactor the code: After the test has passed, you can refactor the code to improve its design and maintainability. For example, you might rename the Add method to Sum to make it more descriptive.

```
public class Calculator
{
    public int Sum(int x, int y)
    {
        return x + y;
    }
}

```
Repeat the process: You then repeat the process with another test until all the required functionality has been implemented.