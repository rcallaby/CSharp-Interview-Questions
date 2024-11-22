# Question 28 - General Questions

## What are reserved words in C#? Can you give me an example?

### **What Are Reserved Words in C#?**

Reserved words in C# are keywords that have special meaning to the compiler. They are part of the C# language syntax and cannot be used as identifiers (e.g., variable names, class names, method names) unless prefixed with the `@` symbol. These words are predefined and reserved for specific functionalities in the language.

---

### **Categories of Reserved Words**

C# reserved words can be grouped into several categories based on their purpose:

1. **Keywords for Data Types**  
   - `int`, `string`, `bool`, `float`, `double`, `decimal`, `char`, `byte`, `long`, etc.

2. **Control Flow Keywords**  
   - `if`, `else`, `switch`, `case`, `for`, `while`, `do`, `break`, `continue`, `return`, etc.

3. **Access Modifiers**  
   - `public`, `private`, `protected`, `internal`, `sealed`, etc.

4. **Class and Method Declaration Keywords**  
   - `class`, `struct`, `interface`, `enum`, `namespace`, `abstract`, `virtual`, `override`, etc.

5. **Exception Handling**  
   - `try`, `catch`, `finally`, `throw`, etc.

6. **Other Special Purpose Keywords**  
   - `this`, `base`, `new`, `static`, `const`, `readonly`, `sizeof`, `typeof`, etc.

7. **Contextual Keywords** (Used in specific contexts but not reserved globally)  
   - `var`, `dynamic`, `async`, `await`, `partial`, `yield`, etc.

---

### **Example: Reserved Word Usage in C#**

Here’s a basic example using reserved words:

```csharp
using System;

class Program
{
    public static void Main()
    {
        int number = 42;        // Reserved word: `int`
        if (number > 0)         // Reserved word: `if`
        {
            Console.WriteLine("The number is positive.");
        }
        else                    // Reserved word: `else`
        {
            Console.WriteLine("The number is non-positive.");
        }
    }
}
```

In this example, `int`, `if`, and `else` are reserved words with predefined behavior in the language.

---

### **Complete List of Reserved Words in C#**

Here’s a comprehensive list of reserved words:

- **Abstract Modifier**: `abstract`
- **Access Modifiers**: `public`, `private`, `protected`, `internal`
- **Class and Method Declaration**: `class`, `struct`, `interface`, `enum`, `namespace`, `void`
- **Control Flow**: `if`, `else`, `switch`, `case`, `for`, `foreach`, `while`, `do`, `break`, `continue`, `return`, `goto`, `yield`
- **Data Types**: `bool`, `byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, `decimal`, `string`, `char`, `object`, `dynamic`, `var`
- **Exception Handling**: `try`, `catch`, `finally`, `throw`
- **Operators and Miscellaneous**: `is`, `as`, `new`, `sizeof`, `typeof`, `checked`, `unchecked`, `default`, `delegate`, `event`, `base`, `this`, `null`, `true`, `false`
- **Other**: `lock`, `using`, `out`, `ref`, `in`, `params`, `static`, `virtual`, `override`, `readonly`, `const`, `volatile`, `sealed`, `fixed`, `unsafe`

---

### **Using Reserved Words as Identifiers**

If you need to use a reserved word as an identifier, prefix it with the `@` symbol:

```csharp
int @class = 10;   // Valid, but not recommended
Console.WriteLine(@class);
```

---

By understanding and correctly using reserved words, you can write more readable and syntactically correct C# programs. 