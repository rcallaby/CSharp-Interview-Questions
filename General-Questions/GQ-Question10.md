# Question 10 - General Questions

## What is the difference between a value type and a reference type in C#?

In C#, value types and reference types are two different kinds of data types that determine how a variable's data is stored in memory.

Value types are types that hold their value directly in memory. When you create a variable of a value type, a copy of the value is created and stored in memory. This means that each variable has its own copy of the data, and changing the value of one variable does not affect the value of any other variable. Examples of value types include numeric types (int, float, double, etc.), char, bool, and enum.

On the other hand, reference types are types that hold a reference (a pointer) to the memory location where the actual data is stored. When you create a variable of a reference type, the variable itself only contains a reference to the data, not the data itself. This means that multiple variables can refer to the same data in memory, and changing the data through one variable affects all other variables that reference the same data. Examples of reference types include class, array, delegate, and interface types.

In summary, the main difference between value types and reference types in C# is that value types store their data directly in memory, while reference types store a reference to the memory location where the data is stored.