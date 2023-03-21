# Question 5 - Clean Code

## Can you give an example of how to write self-explanatory code in C#?

 Here's an example of writing self-explanatory code in C#:

 ```
 using System;

namespace SelfExplanatoryCodeExample
{
    class Program
    {
        static void Main(string[] args)
        {
            int maxValue = GetLargestNumber(10, 20, 30);
            Console.WriteLine("The largest number is: " + maxValue);
        }

        static int GetLargestNumber(int num1, int num2, int num3)
        {
            // Use Math.Max to get the largest number from the three inputs
            return Math.Max(num1, Math.Max(num2, num3));
        }
    }
}

```
In this example, the code is self-explanatory because the names of variables, methods, and classes are descriptive and convey the purpose of each part of the code. The method GetLargestNumber takes three int inputs and returns the largest of the three numbers using the Math.Max method, which is clear from the name of the method. The code is also well-commented, providing further clarification if needed.
