# Question 16 - General Questions

## What is a generic type in C# and why is it used?

In C#, a generic type is a type that is defined with one or more placeholders for its type parameters, which can be replaced with specific types at the time the type is instantiated.

For example, consider a simple generic class called List<T>. The T in this class definition is a type parameter, which can be replaced with any specific type when an instance of the List<T> class is created. For example, you can create a list of integers by instantiating List<int> or a list of strings by instantiating List<string>.

Generics are used in C# to create more flexible and reusable code. By defining a generic class or method, you can write code that works with any type that meets certain requirements, rather than writing separate code for each type. This can help reduce code duplication and improve maintainability.

Generics are also used to provide type safety at compile time. By specifying the type parameter when instantiating a generic class, the C# compiler can ensure that the code only uses that specific type, which helps prevent runtime errors that could occur with type mismatches.