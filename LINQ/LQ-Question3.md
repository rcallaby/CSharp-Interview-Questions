# Question 3 - LINQ

## Can you give an example of using LINQ to filter data in a collection?

Here's an example of using LINQ to filter data in a collection of strings:

```
using System;
using System.Collections.Generic;
using System.Linq;

class Program
{
    static void Main()
    {
        // create a collection of strings
        List<string> words = new List<string> { "apple", "banana", "cherry", "date", "elderberry" };

        // use LINQ to filter the collection to only include strings starting with "c"
        IEnumerable<string> filteredWords = from word in words
                                            where word.StartsWith("c")
                                            select word;

        // print the filtered words
        foreach (string word in filteredWords)
        {
            Console.WriteLine(word);
        }
    }
}

```
In this example, we first create a collection of strings called words. We then use LINQ to filter the collection to only include strings that start with the letter "c". We do this by using the where clause to specify a condition for the filtering, and the select clause to specify which elements of the collection we want to include in the result. Finally, we print out the filtered words using a foreach loop. The output of this program will be:

```
cherry

```
because "cherry" is the only string in the words collection that starts with "c"

