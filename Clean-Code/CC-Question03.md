# Question 3 - Clean Code

## What are some best practices for naming conventions in C#?

In C#, naming conventions are guidelines for naming identifiers such as variables, types, methods, properties, and namespaces. The following are some best practices for naming conventions in C#:

PascalCase: Use PascalCase for naming public types, namespaces, and non-private members (e.g. methods, properties, events, etc.). Example: "MyClass", "MyMethod", "MyProperty".

camelCase: Use camelCase for naming private fields and method arguments. Example: "privateField", "methodArgument".

Use descriptive names: Names should describe the purpose of the identifier. Avoid using abbreviations unless they are widely recognized.

Avoid using single letter names: Single letter names can be confusing and should be avoided except in cases where they are widely recognized (e.g. "i" as a loop index).

Use prefixes to indicate the type of the member: For example, use "m_" as a prefix for private fields, "s_" as a prefix for static fields, and "c_" as a prefix for constants.

Avoid using Hungarian notation: Hungarian notation is an old naming convention that involves adding type information to the beginning of an identifier name. It is not recommended in C#.

Namespace names: Namespace names should be all lowercase, with multiple words separated by dots (periods). Example: "myapp.utils".

Interfaces: Interface names should start with the letter "I" and be in PascalCase. Example: "IMyInterface".

Constants: Constant names should be in uppercase and separated by an underscore. Example: "MY_CONSTANT".

Exception classes: Exception class names should end with the word "Exception". Example: "MyException".

It is important to consistently follow these naming conventions in order to maintain a consistent and readable codebase.