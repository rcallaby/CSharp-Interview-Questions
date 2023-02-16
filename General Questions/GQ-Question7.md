# Question 7 - General Questions

## Can you explain the difference between an abstract class and an interface in C#?

In C#, an abstract class and an interface are both used to define contracts for classes to implement, but they have some differences.

An abstract class is a class that cannot be instantiated on its own and is intended to be subclassed. It can contain both abstract and non-abstract (concrete) methods and can also have member variables. Abstract methods are declared without an implementation and are intended to be overridden by the subclasses. Non-abstract methods have an implementation and can be inherited by the subclasses or overridden if necessary. An abstract class can also provide default implementations for some methods.

An interface, on the other hand, is a contract that defines a set of methods and properties that a class must implement. It cannot contain any implementation code or member variables. An interface only declares the method signature, return type, and parameters, without providing any implementation. Any class that implements an interface must provide an implementation for all the methods and properties declared in the interface.

Here are some key differences between an abstract class and an interface in C#:

Instantiation: An abstract class cannot be instantiated directly while an interface cannot be instantiated at all.

Inheritance: A class can only inherit from one abstract class, but it can implement multiple interfaces.

Abstract methods: An abstract class can contain both abstract and non-abstract methods, but an interface can only contain abstract methods.

Access modifiers: An abstract class can have access modifiers for its members, while an interface's members are always public.

Default implementation: An abstract class can provide default implementations for some methods, but an interface cannot.

In general, abstract classes are used when you want to provide a default implementation for some of the methods or when you need to define member variables, while interfaces are used when you want to define a contract that multiple classes can implement.