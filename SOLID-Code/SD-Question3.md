# Question 3 - SOLID

## How do you avoid Primitive Obsession when designing C# classes, and what are the benefits of doing so?

Primitive Obsession is a code smell that occurs when a programmer uses primitive data types excessively, instead of creating custom classes to represent concepts in the domain. This can lead to code that is difficult to maintain, understand, and extend, as well as a lack of encapsulation and data consistency.

To avoid Primitive Obsession when designing C# classes, here are some guidelines that can be followed:

Identify the concepts in the domain: Start by identifying the concepts that are important to the domain, and create custom classes to represent them. For example, instead of using integers to represent employee IDs, create an EmployeeId class.

Use value objects: Use value objects to represent concepts that have value semantics, such as dates, money, and addresses. Value objects are immutable and can be compared by their value, which makes them safer and easier to use.

Use enums: Use enums to represent concepts that have a limited set of values, such as the days of the week, the months of the year, or the status of an order.

Use interfaces: Use interfaces to define contracts that classes must implement. This promotes loose coupling and allows for easier testing and extension.

Use encapsulation: Encapsulate the behavior of classes and hide their internal state. This reduces the complexity of the code and makes it easier to change and maintain.

The benefits of avoiding Primitive Obsession when designing C# classes are numerous. By using custom classes to represent concepts in the domain, the code becomes more expressive, readable, and maintainable. It also reduces the risk of bugs, as the behavior and constraints of the domain concepts are enforced by the classes. Additionally, it allows for easier extension and evolution of the code, as the concepts can be easily modified and adapted to changing requirements.