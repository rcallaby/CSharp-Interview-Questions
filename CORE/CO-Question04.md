# CORE - Question 04 - Explain the difference between Finalize vs Dispose in .Net CORE?

In .NET Core (and the .NET ecosystem in general), both **`Finalize`** and **`Dispose`** are used to **release unmanaged resources**, but they serve different purposes and operate in very different ways.

Let’s break it down with simple language, comparisons, code examples, and when to use which.

---

## Finalize vs Dispose: Quick Comparison

| Feature         | `Finalize`                           | `Dispose`                                   |
| --------------- | ------------------------------------ | ------------------------------------------- |
| Belongs to      | Object class (via `~Destructor()`)   | `IDisposable` interface                     |
| Triggered by    | **Garbage Collector (GC)**           | **User code (manually)**                    |
| Deterministic?  | ❌ No – You don’t know *when* it runs | ✅ Yes – You decide *when* it runs           |
| Purpose         | Cleanup **unmanaged** resources      | Cleanup **managed or unmanaged** resources  |
| Performance     | Slower – adds GC overhead            | Faster – avoids finalization queue          |
| Override?       | Override `Finalize()` via destructor | Implement `Dispose()`                       |
| Recommended Use | Only if unmanaged resources are used | Always when holding resources (e.g., files) |

---

## What is `Dispose()`?

The `Dispose()` method comes from the `IDisposable` interface. You use it to **explicitly clean up resources**, especially when you're done with something like a file, database connection, or memory stream.

### Example:

```csharp
public class FileLogger : IDisposable
{
    private StreamWriter _writer;

    public FileLogger(string path)
    {
        _writer = new StreamWriter(path);
    }

    public void Log(string message)
    {
        _writer.WriteLine(message);
    }

    public void Dispose()
    {
        _writer?.Dispose(); // Clean up managed resource
        Console.WriteLine("Dispose called");
    }
}
```

### Usage:

```csharp
using (var logger = new FileLogger("log.txt"))
{
    logger.Log("Hello, world!");
}
// Dispose is called automatically at the end of the using block
```

This is **deterministic**: you know exactly when the cleanup happens.

---

## What is `Finalize()`?

The `Finalize()` method is defined in the base `Object` class and is **automatically called by the garbage collector**, *if and only if* you override it using a **destructor syntax** (`~ClassName()`).

You **cannot call it manually**.

### Example:

```csharp
public class NativeResourceHolder
{
    IntPtr unmanagedMemory;

    public NativeResourceHolder()
    {
        unmanagedMemory = Marshal.AllocHGlobal(100);
    }

    ~NativeResourceHolder()
    {
        Console.WriteLine("Finalizer called");
        Marshal.FreeHGlobal(unmanagedMemory);
    }
}
```

### Usage:

```csharp
var obj = new NativeResourceHolder();
// No Dispose, so Finalizer will eventually run... someday...
obj = null;
GC.Collect();
GC.WaitForPendingFinalizers(); // Forcing GC for demo only
```

You **don’t know when** `Finalize()` will run — maybe immediately, maybe much later. It's a **safety net**.

---

## 🛠 Best Practice: Combine Both (`Dispose` + `Finalize`)

If you're dealing with **unmanaged resources**, use **both** in a safe pattern:

### Example: Proper Disposable Pattern

```csharp
public class ResourceHandler : IDisposable
{
    private IntPtr _unmanaged;
    private bool _disposed;

    public ResourceHandler()
    {
        _unmanaged = Marshal.AllocHGlobal(100);
    }

    ~ResourceHandler()
    {
        Dispose(false); // called by Finalizer
    }

    public void Dispose()
    {
        Dispose(true);
        GC.SuppressFinalize(this); // Stop finalizer from running
    }

    protected virtual void Dispose(bool disposing)
    {
        if (_disposed) return;

        if (disposing)
        {
            // dispose managed resources here if any
        }

        if (_unmanaged != IntPtr.Zero)
        {
            Marshal.FreeHGlobal(_unmanaged); // cleanup unmanaged
            _unmanaged = IntPtr.Zero;
        }

        _disposed = true;
    }
}
```

✅ `Dispose()` for deterministic cleanup.
✅ `Finalize()` as a safety net if user forgot to call `Dispose()`.

---

## Analogy

* `Dispose()` is like **you turning off the light when you leave the room.**
* `Finalize()` is like **someone else turning off the light after you’ve left and forgotten.**

---

## Summary

| Use Case                                               | Use                        |
| ------------------------------------------------------ | -------------------------- |
| Managed resources only (e.g., `List<T>`, `FileStream`) | `Dispose()`                |
| Unmanaged resources (e.g., native memory, handles)     | `Dispose()` + `Finalize()` |
| Only as a safety net                                   | `Finalize()`               |

---

## .NET Core Bonus: `IAsyncDisposable`

.NET Core adds support for **async resource cleanup** via `IAsyncDisposable`.

```csharp
public async ValueTask DisposeAsync()
{
    await _stream.DisposeAsync(); // for async streams etc.
}
```

Use it with `await using`:

```csharp
await using var resource = new SomeAsyncDisposable();
```


