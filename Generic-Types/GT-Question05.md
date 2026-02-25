# Question 5 - Generic Types

## Can you give an example of a generic method in C#?

Here's an example of a generic method in C#:

```
public static T FindMax<T>(T[] array) where T : IComparable<T>
{
    if (array == null)
    {
        throw new ArgumentNullException("array");
    }

    if (array.Length == 0)
    {
        throw new ArgumentException("The array must not be empty.", "array");
    }

    T max = array[0];

    for (int i = 1; i < array.Length; i++)
    {
        if (array[i].CompareTo(max) > 0)
        {
            max = array[i];
        }
    }

    return max;
}

```
This method takes an array of type T, and returns the maximum element of the array. The type parameter T is declared in angle brackets (< and >), and the method signature uses this type parameter to specify the type of the array parameter and the return type.

The where T : IComparable<T> constraint specifies that T must implement the IComparable<T> interface, which allows the method to compare elements of the array.

By using a generic method like this, we can write code that works with different types of objects, without having to write separate versions of the method for each type.