# Question 1 - LINQ

## What is LINQ and how does it work in C#?

LINQ (Language Integrated Query) is a feature in C# that allows developers to query data from different data sources using a unified syntax. LINQ enables developers to write complex queries that can be executed against different types of data sources such as in-memory objects, databases, XML documents, and more.

LINQ works by providing a set of query operators that allow developers to write queries in a declarative style. These query operators are defined as extension methods on IEnumerable<T> and IQueryable<T> interfaces. The query operators are designed to work with different data sources, and they can be chained together to build complex queries.

Here's an example of how LINQ can be used to query a collection of objects:

```
var students = new List<Student>
{
    new Student { Name = "John", Age = 21, Grade = "A" },
    new Student { Name = "Mary", Age = 22, Grade = "B" },
    new Student { Name = "Jane", Age = 20, Grade = "A" }
};

var aStudents = students.Where(s => s.Grade == "A").ToList();

```
In the above example, we have a list of Student objects, and we use the Where operator to filter the students who have a grade of "A". The ToList operator is used to convert the result into a list.

LINQ is a powerful tool for querying data, and it can greatly simplify the process of writing complex queries. By providing a unified syntax for querying different types of data sources, LINQ makes it easier to write code that is more concise and easier to read.