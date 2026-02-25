# Question 8 - General Questions

## What is a constructor in C# and what are its different types?

In C#, a constructor is a special method that is called when an object of a class is created. The purpose of a constructor is to initialize the state of an object with some initial values.

C# supports two types of constructors:

Instance Constructors: An instance constructor is used to initialize the instance variables of a class. It is called when an object of the class is created using the new keyword. An instance constructor has the same name as the class and does not have a return type.
Here is an example of an instance constructor:

```
public class MyClass {
    public int x;
    public int y;

    public MyClass(int x, int y) {
        this.x = x;
        this.y = y;
    }
}

```
Static Constructors: A static constructor is used to initialize the static variables of a class. It is called only once, when the class is first used. A static constructor has the same name as the class and does not have any parameters.
Here is an example of a static constructor:

```
public class MyClass {
    public static int x;
    public static int y;

    static MyClass() {
        x = 10;
        y = 20;
    }
}
```
Note that a class can have multiple constructors, but they must have different signatures (i.e., different parameter lists). This is known as constructor overloading.
