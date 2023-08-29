# Question 3 - SOLID

## How do you avoid Primitive Obsession when designing C# classes, and what are the benefits of doing so?

Primitive Obsession is a code smell in software development where simple data types, also known as primitive types (like integers, strings, booleans), are used excessively in a program instead of creating dedicated classes to represent specific concepts or domains. This can lead to a variety of issues, including reduced readability, maintainability, and extensibility of the codebase. To avoid Primitive Obsession in C# classes, you can follow several guidelines:

Identify Concepts: Identify the concepts or domain-specific entities in your codebase. These could be anything from dates and times to addresses or monetary amounts.

Create Meaningful Classes: Instead of using primitive types to represent these concepts, create meaningful classes to encapsulate the data and behavior related to those concepts.

Encapsulate Logic: Move logic related to these concepts into the respective classes. This can help improve code organization and readability.

Provide Abstraction: Design classes that abstract away the complexities of the underlying data. This can lead to clearer and more expressive code.

Use Strong Typing: By using custom classes, you introduce strong typing, which helps catch errors at compile-time rather than runtime.

Data Validation: Implement validation and data consistency checks within the class methods to ensure that the data adheres to the expected rules.

Avoid Repetition: By centralizing the logic within these classes, you can avoid repeating the same validation or transformation logic throughout your codebase.

Enable Extension: Designing classes with proper encapsulation allows you to easily extend their functionality in the future without affecting other parts of the codebase.

Example:

Let's consider an example of a system that deals with orders. Instead of using primitive types to represent order-related data, we can create meaningful classes to avoid Primitive Obsession:

```
// Primitive Obsession (Avoid this)
public class Order
{
    public int OrderId { get; set; }
    public string CustomerName { get; set; }
    public decimal TotalAmount { get; set; }
    // ... other properties
}

// Improved: Using dedicated classes
public class Order
{
    public int OrderId { get; set; }
    public Customer Customer { get; set; }
    public Money TotalAmount { get; set; }
    // ... other properties
}

public class Customer
{
    public int CustomerId { get; set; }
    public string Name { get; set; }
    // ... other properties
}

public class Money
{
    public decimal Amount { get; set; }
    public string Currency { get; set; }
    // ... other properties and validation logic
}

```
In this improved example, we've introduced dedicated classes for Customer and Money. By using these classes, we're providing clear abstractions for these concepts, enabling better validation and encapsulation of their respective logic. This leads to more readable, maintainable, and extensible code.

Benefits of avoiding Primitive Obsession:

Readability: Code using dedicated classes is more self-explanatory and easier to understand.
Maintainability: Changes and updates are localized to specific classes, reducing the risk of introducing bugs.
Extensibility: New features or behaviors can be added to the classes without affecting other parts of the codebase.
Validation and Consistency: Data validation and consistency checks can be centralized within the class methods.
Type Safety: Strong typing helps catch errors at compile-time.
Encapsulation: Logic related to a concept is contained within its respective class, improving code organization.

Overall, avoiding Primitive Obsession leads to more robust, maintainable, and understandable code.