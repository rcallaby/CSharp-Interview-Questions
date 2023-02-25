# Question 15  - General Questions

## Can you explain the difference between a static and an instance method in C#?

In C#, a method is a block of code that performs a specific task. There are two types of methods in C#: static and instance methods.

Static Methods:
A static method is a method that is associated with the class rather than an instance of the class. It can be called without creating an instance of the class. In other words, it's a method that belongs to the type itself and not to an instance of the type.

Here is an example of a static method:

```
public static int Add(int num1, int num2)
{
    return num1 + num2;
}

```
In this example, the Add method is a static method. It can be called using the class name, like this:

```
int sum = MyClass.Add(5, 10);

```
Instance Methods:
An instance method is a method that is associated with an instance of a class. It can only be called on an instance of the class, after an object of the class has been created.

Here is an example of an instance method:

```
public void DisplayMessage(string message)
{
    Console.WriteLine(message);
}

```
In this example, the DisplayMessage method is an instance method. It can only be called on an instance of the class, like this:

```
MyClass obj = new MyClass();
obj.DisplayMessage("Hello, world!");

```
In summary, the main difference between static and instance methods in C# is that static methods are associated with the class, while instance methods are associated with an instance of the class.