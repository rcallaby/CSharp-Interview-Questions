# Question 9 - Generic Types

## How can you implement generic algorithms in C#?

In C#, you can implement generic algorithms using generic types and methods. Generics allow you to write code that can work with different types of data, without having to rewrite the code for each type. Here are the steps to implement a generic algorithm in C#:

Define a generic type or method by using the angle brackets syntax "<T>". The "T" can be replaced by any identifier, and it represents the type parameter.

Use the type parameter "T" in the code to indicate the type of the data that the algorithm will work with.

Instantiate the generic type or method with a specific type when you use it in your program.

For example, let's say you want to create a generic method that sorts an array of any type. Here's how you can implement it:

```
public static void GenericSort<T>(T[] array) where T : IComparable<T>
{
    for (int i = 0; i < array.Length; i++)
    {
        for (int j = i + 1; j < array.Length; j++)
        {
            if (array[i].CompareTo(array[j]) > 0)
            {
                T temp = array[i];
                array[i] = array[j];
                array[j] = temp;
            }
        }
    }
}

```
In this example, the method has a type parameter "T", which represents the type of the elements in the array. The "where" keyword is used to specify that the type parameter must implement the "IComparable<T>" interface, so that the method can compare the elements.

To use this method with an array of integers, for example, you would call it like this:

```
int[] numbers = { 3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5 };
GenericSort(numbers);

```
To use it with an array of strings, you would call it like this:

```
string[] words = { "apple", "banana", "cherry", "date", "elderberry" };
GenericSort(words);
```
By using generic types and methods in C#, you can write more flexible and reusable code that works with different types of data.

