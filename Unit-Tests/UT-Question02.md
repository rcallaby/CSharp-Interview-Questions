# Question 2 - Unit Tests

## Can you explain the different types of unit tests that can be performed in C#?

In C#, there are several types of unit tests that can be performed. Here are some of the most common types:

Test initialization and cleanup methods: These methods are used to set up any data or resources that your tests will need before they run, and to clean up after the tests have finished. They are usually marked with [TestInitialize] and [TestCleanup] attributes.

Assert methods: These methods are used to check that the results of your tests are what you expect them to be. Some common assert methods include Assert.AreEqual(), Assert.IsTrue(), and Assert.IsFalse().

Parameterized tests: These are tests that are designed to run with multiple sets of inputs. You can use the [TestCase] attribute to specify the different input values that your test should use.

Test suites: Test suites are collections of related tests that can be run together. You can use the [TestClass] attribute to mark a class as a test suite, and then use the [TestMethod] attribute to mark each individual test method.

Mocking and stubbing: These techniques are used to isolate the code being tested from its dependencies. You can use tools like Moq or RhinoMocks to create mock objects that simulate the behavior of your dependencies.

Integration tests: These are tests that verify that different parts of your application work correctly together. Integration tests often involve setting up a database or other external resource to test against.

It's important to note that these types of tests are not mutually exclusive - in fact, many tests will involve a combination of these techniques. The key is to choose the right types of tests for the code you're working with, and to make sure that your tests are comprehensive and effective.