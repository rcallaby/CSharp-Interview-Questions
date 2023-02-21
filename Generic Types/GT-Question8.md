# Question 8 - Generic Types

## Can you explain the concept of type constraints in C#?

Type constraints in C# provide a way to restrict the types that can be used as type arguments for generic type parameters. When defining a generic class or method, you can specify a type constraint that restricts the set of types that can be used as type arguments.

Here's an example of a generic method with a type constraint:

```
public static T Find<T>(T[] array, Predicate<T> match) where T : class
{
    foreach (T item in array)
    {
        if (match(item))
        {
            return item;
        }
    }
    return null;
}

```
In this example, the where T : class clause specifies that the type argument T must be a reference type. This means that the method can't be used with value types like int or double.

Other possible type constraints include:

where T : struct: Specifies that the type argument T must be a value type.
where T : new(): Specifies that the type argument T must have a public parameterless constructor.
where T : MyInterface: Specifies that the type argument T must implement the interface MyInterface.
Type constraints can help make your code more robust by ensuring that the types used in a generic class or method are compatible with the functionality it provides.