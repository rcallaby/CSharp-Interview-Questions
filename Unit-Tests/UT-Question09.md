# Question 9 - Unit Tests

## How do you measure the code coverage of your unit tests, and what is considered an acceptable level of code coverage in C#?

Code coverage is a metric that measures how much of your code is executed by your automated tests. In C#, you can measure code coverage using tools like Visual Studio's built-in Test Explorer or third-party tools like OpenCover and dotCover.

To measure code coverage in Visual Studio, follow these steps:

+ Build your solution in "Debug" mode.
+ Open the Test Explorer window (Test > Windows > Test Explorer).
+ Run your unit tests by selecting them in the Test Explorer and clicking the "Run" button.
+ Once the tests have completed, click the "Code Coverage" button in the Test Explorer to view the code coverage results.
+ In terms of what is considered an acceptable level of code coverage in C#, there is no one-size-fits-all answer. The level of code coverage that is appropriate for your project will depend on a variety of factors, such as the complexity of your code, the risk associated with defects in your code, and the level of confidence you need in your tests.

However, as a general rule of thumb, a code coverage level of at least 80% is often considered a good starting point for most projects. This means that your tests should cover 80% of the lines of code in your application. Keep in mind that code coverage is just one measure of the effectiveness of your tests, and it's important to also consider other factors like the quality of your test cases and the reliability of your test infrastructure.