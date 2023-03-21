# Question 10 - Clean Code

## What are some common anti-patterns in C# and how can they be avoided to write clean code?

Anti-patterns are certain practices or design approaches that seem good initially but lead to negative consequences in the long run, making the code less maintainable, testable and harder to understand. Here are a few common anti-patterns in C# and how to avoid them:

Magic Strings: Magic Strings are hardcoded string values that are used throughout the code, making it difficult to change without breaking the code. To avoid this, you can use constants, enums or named values to store the strings.

Overcomplicated Code: Overcomplicated code can be hard to read and maintain, making it difficult for other developers to understand and make changes. To avoid this, you can use simple, clear and concise code, that is easy to read and follow.

Hardcoding Values: Hardcoded values in the code are difficult to change and can lead to bugs. To avoid this, you can use variables, constants, or configuration files to store values that might change.

Using Primitive Obsession: Primitive obsession is when primitive data types are used instead of creating custom classes that better describe the data. This can lead to data-related problems and make the code difficult to understand. To avoid this, you can create custom classes or enums that describe the data.

Ignoring Exceptions: Ignoring exceptions in code can lead to unexpected behavior and make it difficult to understand what's going wrong. To avoid this, you can catch and handle exceptions appropriately, or let them propagate up the call stack if they are truly exceptional cases.

Not using Interfaces: Interfaces define contracts that can be implemented by multiple classes, providing loose coupling and making the code more maintainable. To avoid this, you can use interfaces to define contracts that can be implemented by multiple classes, instead of tightly coupling classes together.

Not following SOLID principles: SOLID principles are a set of design principles that provide a framework for creating maintainable and scalable code. To avoid this, you can follow the SOLID principles to ensure your code is maintainable and scalable.

By avoiding these anti-patterns, you can write clean code that is easy to read, maintain and extend.