# Question 9 - Clean Code

## How can you write code that follows the DRY (Don't Repeat Yourself) principle in C#?

The DRY (Don't Repeat Yourself) principle is a software development principle that states that "Every piece of knowledge must have a single, unambiguous, authoritative representation within a system."

In C#, you can follow the DRY principle by:

Extracting common logic into methods or functions: You can extract commonly used logic into methods or functions and call them whenever you need to perform that logic. This helps reduce duplication and makes your code easier to maintain.

Using inheritance: You can create a base class that contains common functionality, and then inherit from it to create more specific classes. This allows you to reuse code and ensure that all related classes have the same behavior.

Using interfaces: Interfaces allow you to define a contract that multiple classes can implement. This allows you to reuse code without duplicating it.

Using design patterns: Design patterns are reusable solutions to common problems. By using design patterns, you can ensure that your code is DRY and follows best practices.

Using libraries and frameworks: Reuse existing libraries and frameworks to avoid reinventing the wheel. This helps reduce duplication and improve the quality of your code.

By following these techniques, you can write code that follows the DRY principle and is more maintainable, readable, and scalable.