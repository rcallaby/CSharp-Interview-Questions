# Question 8 - Clean Code

## Can you explain the difference between writing procedural and object-oriented code in C#?

Procedural code, also known as imperative programming, focuses on writing code as a series of steps to perform a specific task. In procedural programming, the code is organized around procedures (also known as functions or subroutines) that perform specific tasks. The focus is on what needs to be done and how it needs to be done, rather than on the data being processed.

On the other hand, object-oriented programming (OOP) focuses on organizing code around objects, which are instances of classes. In OOP, objects encapsulate data and behavior, and the interaction between objects is achieved through method calls. The focus is on the data being processed and the methods that operate on that data, rather than on the steps taken to perform a specific task.

In C#, the difference between procedural and object-oriented code is largely a matter of style. Both paradigms can be used in C#, and you can write procedural code using C#, just as you can write object-oriented code using other languages. However, C# is designed to support object-oriented programming, and most C# code is written using OOP principles.

Here is an example to help illustrate the difference between procedural and object-oriented code in C#:

```
//Procedural code in C#
using System;

namespace ProceduralProgramming
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Enter the radius of a circle: ");
            double radius = Convert.ToDouble(Console.ReadLine());

            double area = CalculateCircleArea(radius);
            Console.WriteLine("The area of the circle is: " + area);
        }

        static double CalculateCircleArea(double r)
        {
            double area = Math.PI * r * r;
            return area;
        }
    }
}

// Object-oriented code in C#
using System;

namespace ObjectOrientedProgramming
{
    class Circle
    {
        private double radius;

        public Circle(double r)
        {
            radius = r;
        }

        public double CalculateArea()
        {
            return Math.PI * radius * radius;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Enter the radius of a circle: ");
            double radius = Convert.ToDouble(Console.ReadLine());

            Circle circle = new Circle(radius);
            double area = circle.CalculateArea();
            Console.WriteLine("The area of the circle is: " + area);
        }
    }
}

```
As you can see, the object-oriented code is organized around a Circle class, which encapsulates the data (the radius of the circle) and the behavior (the method to calculate the area of the circle). In contrast, the procedural code is organized around procedures (functions) that perform specific tasks.

