# Question 6 - Generic Types

## What are the restrictions for using generic types in C#?

In C#, generic types are a powerful feature of the language, but there are restrictions on their use. Let's explore these restrictions along with source code examples.

---

### 1. **Value Types and Nullable Constraints**
Generic types must comply with certain constraints, particularly when dealing with value types (`struct`) and nullable types (`Nullable<T>`). Generics cannot directly enforce a value type constraint without the `struct` constraint.

**Example:**

```csharp
// Allowed: Restricting to value types using struct
public class ValueHolder<T> where T : struct
{
    public T Value { get; set; }
}

// Usage:
var intHolder = new ValueHolder<int>(); // Valid
// var objHolder = new ValueHolder<object>(); // Compilation Error: object is not a value type
```

---

### 2. **Reference Type Constraints**
You can restrict generic types to reference types (`class`). This ensures the generic type is always a reference type.

**Example:**

```csharp
// Allowed: Restricting to reference types using class
public class ReferenceHolder<T> where T : class
{
    public T Value { get; set; }
}

// Usage:
var stringHolder = new ReferenceHolder<string>(); // Valid
// var intHolder = new ReferenceHolder<int>(); // Compilation Error: int is not a reference type
```

---

### 3. **Default Constructor Constraint**
You can specify that the generic type must have a parameterless constructor using the `new()` constraint. However, this cannot be combined with `struct` because value types inherently have a parameterless constructor.

**Example:**

```csharp
// Allowed: Restricting to types with a parameterless constructor
public class Creator<T> where T : new()
{
    public T CreateInstance()
    {
        return new T();
    }
}

// Usage:
var creator = new Creator<StringBuilder>(); // Valid
// var creator = new Creator<string>(); // Compilation Error: string does not have a parameterless constructor
```

---

### 4. **Multiple Constraints**
You can combine constraints, such as enforcing that a generic type is both a reference type (`class`) and implements specific interfaces or has a parameterless constructor.

**Example:**

```csharp
// Allowed: Multiple constraints
public class Processor<T> where T : class, IDisposable, new()
{
    public void Process(T obj)
    {
        obj.Dispose();
    }
}

// Usage:
var processor = new Processor<MemoryStream>(); // Valid
// var processor = new Processor<int>(); // Compilation Error: int does not meet the constraints
```

---

### 5. **Static Members in Generic Types**
Static members in generic types are specific to the generic type argument. Different type arguments result in different static member instances.

**Example:**

```csharp
// Static members are separate for each generic type
public class Counter<T>
{
    public static int Count = 0;
}

// Usage:
Counter<int>.Count++;    // Increment for int
Counter<string>.Count++; // Increment for string
Console.WriteLine(Counter<int>.Count);    // Output: 1
Console.WriteLine(Counter<string>.Count); // Output: 1
```

---

### 6. **Inheritance and Base Class Constraints**
Generics can be constrained to derive from a specific class or implement a specific interface.

**Example:**

```csharp
// Allowed: Base class or interface constraint
public class BaseClass { }
public class DerivedClass : BaseClass { }

public class GenericHolder<T> where T : BaseClass
{
    public T Value { get; set; }
}

// Usage:
var holder = new GenericHolder<DerivedClass>(); // Valid
// var holder = new GenericHolder<string>(); // Compilation Error: string is not derived from BaseClass
```

---

### 7. **Type Parameter Count Must Match**
When using generic types, the number of type parameters in the definition and instantiation must match.

**Example:**

```csharp
public class Pair<T1, T2>
{
    public T1 First { get; set; }
    public T2 Second { get; set; }
}

// Usage:
var pair = new Pair<int, string>(); // Valid
// var invalidPair = new Pair<int>(); // Compilation Error: Missing type parameter
```

---

### 8. **Generics and Operators**
Generic types cannot use arithmetic or comparison operators (`+`, `-`, `<`, etc.) unless explicitly implemented. Generics do not support implicit operator constraints.

**Example:**

```csharp
public class Adder<T>
{
    public T Add(T a, T b)
    {
        // return a + b; // Compilation Error: '+' operator is not defined for type T
        throw new NotImplementedException();
    }
}
```

To work around this, use constraints or implement interfaces like `IAddable`.

---

### 9. **Non-Type Parameters**
Unlike C++ templates, C# generics do not support non-type parameters (e.g., `T[10]`).

**Not Allowed:**

```csharp
// Compilation Error: C# does not support non-type parameters in generics
public class Container<T, int size> { }
```

---

By understanding these restrictions, you can effectively use C# generics while respecting the constraints of the language.