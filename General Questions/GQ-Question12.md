# Question 12 - General Questions 

## What is a delegate in C# and how is it used?

In C#, a delegate is a type that represents a method with a specific signature. It can be used to reference a method and invoke it indirectly, which provides a flexible way of decoupling the caller from the callee.

A delegate declaration defines the signature of the method that it can reference. For example, the following delegate declaration defines a delegate type named MyDelegate that can reference a method that takes two integers as parameters and returns an integer:

```
delegate int MyDelegate(int x, int y);

```
A delegate object can be created by instantiating a delegate type with a method name or a lambda expression that matches the signature of the delegate type. For example, the following code creates a delegate object that references a method named Add:

```
MyDelegate myDelegate = Add;

```
or with a lambda expression:

```
MyDelegate myDelegate = (x, y) => x + y;

```
Once a delegate object is created, it can be invoked like a method. The following code invokes the delegate object created above:

```
int result = myDelegate(1, 2); // result == 3

```
Delegates can also be used as event handlers in C# programs. When an event occurs, the delegate associated with the event is invoked, which can trigger the corresponding event handling code.

Delegates can provide a powerful way to implement flexible and extensible code. They are often used in functional programming and in .NET Framework classes, such as those in the System.Action and System.Func namespaces.