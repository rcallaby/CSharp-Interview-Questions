# Question 15 - Design Patterns

## What is the Flyweight pattern in C# and how is it used to optimize memory usage?

The Flyweight pattern is a software design pattern that is used to optimize memory usage by sharing objects that are identical or similar between multiple clients. The goal of the Flyweight pattern is to minimize memory usage by sharing objects that are frequently used by multiple clients.

In C#, the Flyweight pattern can be implemented by using a factory class that creates and manages shared objects. The factory class maintains a cache of objects and returns a shared object if it already exists. If a requested object does not exist in the cache, the factory class creates a new object and adds it to the cache.

The shared objects are typically represented as classes that define the structure and behavior of the objects. The shared objects must be immutable, meaning that their state cannot be changed once they are created. This allows multiple clients to share the same objects without the risk of data inconsistencies.

The Flyweight pattern is particularly useful in situations where there is a large number of objects that are identical or similar. By sharing objects between multiple clients, the Flyweight pattern can reduce memory usage and improve performance by avoiding the overhead of creating and managing multiple objects.

For example, consider a scenario where a graphical user interface application must display a large number of icons. Each icon is identical in size and shape but may have a different color. By using the Flyweight pattern, the application can create a single object that represents the structure and behavior of an icon and share it between multiple clients. The clients can then set the color of the shared object to achieve the desired appearance.