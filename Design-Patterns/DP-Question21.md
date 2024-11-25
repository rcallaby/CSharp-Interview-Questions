# Question 21 - Design Patterns

## How have the improvements in .Net 9 improved the implementation of design patters in C#?

The improvements introduced in .NET 9 and C# 13 offer several enhancements that significantly impact the implementation of design patterns in C#. One of the most notable improvements is the performance optimizations, such as faster exception handling, loop performance, and RyuJIT improvements. These changes enable developers to focus more on application logic rather than managing performance bottlenecks, making the application of patterns like Singleton, Factory, and Strategy more efficient and scalable.

Additionally, .NET 9 introduces new types, such as `Tensor<T>` for working with AI, which provides an easy way to integrate machine learning models, and `HybridCache` for more efficient caching. These updates open the door for modern design patterns, like the Observer and Proxy patterns, in handling data flows and caching mechanisms in distributed systems.

For example, the improved capabilities of dependency injection in ASP.NET Core can simplify the implementation of the Dependency Injection pattern, making it more robust and suitable for larger applications with multiple services. The hybrid caching approach also aligns well with patterns such as Cache-Aside or Cache-Through, offering optimized caching strategies for modern web applications.

These updates streamline the use of traditional design patterns and also encourage the adoption of more modern patterns suitable for cloud-native and AI-driven applications. For more details on the improvements, you can check out additional resources on .NET 9's new features.

## Source Code examples

Here are examples illustrating improvements in .NET 9, including performance optimizations, dependency injection, and new caching strategies, using C#.

### 1. **Performance Improvement: Faster Exception Handling**

In earlier versions of .NET, exceptions were handled with some overhead that could degrade performance. .NET 9 introduces a faster exception model, allowing better exception handling with less cost. Here's a comparison before and after the optimization.

**Before .NET 9:**
```csharp
try
{
    // Simulate an operation that throws an exception
    throw new InvalidOperationException("Something went wrong.");
}
catch (InvalidOperationException ex)
{
    Console.WriteLine($"Error: {ex.Message}");
}
```
**After .NET 9:**
The syntax remains the same, but .NET 9 optimizes the internal handling of exceptions, reducing the overhead.

```csharp
try
{
    // Simulate an operation that throws an exception
    throw new InvalidOperationException("Something went wrong.");
}
catch (InvalidOperationException ex)
{
    Console.WriteLine($"Error: {ex.Message}");
}
```
*Result*: The exception handling is now more performant, and the system spends less time on stack unwinding, making it faster in large-scale applications.

---

### 2. **Dependency Injection (DI) Improvements**

In .NET 9, Dependency Injection (DI) has become more robust. It's now easier to configure services, making the use of DI patterns in cloud-native apps more streamlined.

**Before .NET 9:**
```csharp
public class SomeService
{
    private readonly IMyService _myService;

    public SomeService(IMyService myService)
    {
        _myService = myService;
    }

    public void Execute()
    {
        _myService.DoWork();
    }
}

public class MyService : IMyService
{
    public void DoWork() => Console.WriteLine("Working...");
}

public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddSingleton<IMyService, MyService>();
        services.AddTransient<SomeService>();
    }
}
```

**After .NET 9:**
.NET 9 allows services to be configured more efficiently with fewer lines of code and a more seamless integration for cloud-native applications. It introduces enhancements in `ConfigureServices`, making it more straightforward.

```csharp
public class SomeService
{
    private readonly IMyService _myService;

    public SomeService(IMyService myService)
    {
        _myService = myService;
    }

    public void Execute()
    {
        _myService.DoWork();
    }
}

public class MyService : IMyService
{
    public void DoWork() => Console.WriteLine("Working...");
}

public class Program
{
    public static void Main(string[] args)
    {
        var builder = WebApplication.CreateBuilder(args);
        
        // Improved DI configuration
        builder.Services.AddSingleton<IMyService, MyService>();
        builder.Services.AddTransient<SomeService>();
        
        var app = builder.Build();
        
        var someService = app.Services.GetRequiredService<SomeService>();
        someService.Execute();
        
        app.Run();
    }
}
```
*Result*: The DI container is optimized for better performance and integration with microservices and cloud-native applications.

---

### 3. **Hybrid Caching API: Cache-Aside Pattern**

.NET 9 introduces the `HybridCache` API, which combines in-process and out-of-process caches. This allows for more efficient caching strategies, such as the Cache-Aside pattern, which is especially useful in modern web apps.

**Before .NET 9:**
```csharp
public class DataService
{
    private readonly ICacheService _cacheService;

    public DataService(ICacheService cacheService)
    {
        _cacheService = cacheService;
    }

    public string GetData(string key)
    {
        var data = _cacheService.Get(key);
        if (data == null)
        {
            data = FetchDataFromDatabase(key);
            _cacheService.Set(key, data);
        }
        return data;
    }

    private string FetchDataFromDatabase(string key) => "Data from DB";
}
```

**After .NET 9:**
.NET 9's `HybridCache` provides a more efficient and scalable approach by combining multiple cache layers.

```csharp
public class DataService
{
    private readonly IHybridCache _hybridCache;

    public DataService(IHybridCache hybridCache)
    {
        _hybridCache = hybridCache;
    }

    public string GetData(string key)
    {
        // Cache-Aside with HybridCache (multi-tier)
        var data = _hybridCache.GetOrAdd(key, _ => FetchDataFromDatabase(key));
        return data;
    }

    private string FetchDataFromDatabase(string key) => "Data from DB";
}
```
*Result*: The use of `HybridCache` significantly improves caching strategies, especially for distributed systems, by utilizing multi-tier storage (in-process and out-of-process).

---

These code examples demonstrate how .NET 9's performance improvements and new features can simplify the implementation of design patterns, such as caching, dependency injection, and error handling. The optimizations not only reduce overhead but also improve scalability and maintainability in modern cloud applications.
