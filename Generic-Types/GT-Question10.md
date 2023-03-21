# Question 10 - Generic Types

## Can you explain the difference between a generic class and a class that uses a generic type as a parameter?

A generic class is a class that is defined with one or more type parameters, which can be used to specify the type of objects that the class will operate on. The type parameters are placeholders for actual types that will be specified when objects of the class are created. For example, in Java, a generic class might be defined like this:

```
public class MyGenericClass<T> {
    // ...
}

```
In this example, the type parameter T can be used within the class to represent the actual type that will be specified when objects of the class are created. For example, MyGenericClass<String> would create objects of the class that operate on String objects.

On the other hand, a class that uses a generic type as a parameter is a class that takes a generic type as an argument when it is constructed or used. This type parameter is typically used to define the type of objects that the class will operate on or to parameterize some other behavior of the class. For example, in Java, a List is a class that uses a generic type as a parameter:

```
List<String> myStringList = new ArrayList<String>();

```
In this example, the List class takes a type parameter String, which specifies that the list will only contain String objects. The ArrayList is a specific implementation of the List interface that uses an array to store its elements.

In summary, a generic class is a class that is defined with one or more type parameters, while a class that uses a generic type as a parameter is a class that takes a generic type as an argument when it is constructed or used.