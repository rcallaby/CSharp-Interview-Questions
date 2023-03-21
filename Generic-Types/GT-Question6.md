# Question 6 - Generic Types

## What are the restrictions for using generic types in C#?

In C#, there are some restrictions on the use of generic types. Here are some of the main ones:

Type parameters cannot be value types: When defining a generic class or method, type parameters cannot be value types such as int or bool. Instead, they must be reference types or nullable value types.

Type parameters cannot be used in certain contexts: Type parameters cannot be used in some contexts, such as in constant fields, operator overloads, or as base classes.

Generic type arguments must be known at compile-time: When using a generic type, the type arguments must be known at compile-time. It is not possible to pass a type argument that is determined at runtime.

Boxing and unboxing: When using a generic type with a value type argument, there is a performance penalty due to boxing and unboxing. This means that the value type is converted to an object reference (boxing) when it is passed as a type argument, and then converted back to a value type (unboxing) when it is used within the generic code.

Inheritance restrictions: There are some restrictions on the inheritance of generic types. For example, a generic class cannot inherit from a non-generic class, and a non-generic class cannot inherit from a generic class with a specific type argument.

These are some of the main restrictions on the use of generic types in C#. However, these restrictions are generally not too limiting, and generic types are a powerful tool for creating reusable and flexible code.