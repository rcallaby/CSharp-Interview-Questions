# CORE - Question 02 - Please tell me what is included in .Net and the reasons why some components aren't included in .Net Core?

Understanding what's included in **.NET Framework** vs what's included (or excluded) in **.NET Core** (and now modern **.NET 5/6/7/8**) reveals a lot about the **goals, trade-offs, and evolution** of the platform.

---

## What’s Included in the Full .NET Framework?

The original **.NET Framework** (1.0–4.8) is a **monolithic**, **Windows-only** platform that includes:

### 🔹 1. **CLR (Common Language Runtime)**

* Garbage Collection
* JIT compilation
* Code Access Security
* Exception handling
* Threading and synchronization

### 🔹 2. **Base Class Library (BCL)**

* `System`, `System.Collections`, `System.IO`, `System.Text`, etc.

### 🔹 3. **Desktop UI Frameworks**

* **Windows Forms (WinForms)**
* **Windows Presentation Foundation (WPF)**

### 🔹 4. **ASP.NET (Classic)**

* Web Forms
* ASP.NET MVC
* ASP.NET Web API

### 🔹 5. **Workflow & Communication**

* **Windows Communication Foundation (WCF)**
* **Windows Workflow Foundation (WF)**

### 🔹 6. **Entity Framework (EF 6)**

* Object-Relational Mapping (ORM)

### 🔹 7. **Global Assembly Cache (GAC)**

* Shared assemblies system-wide

### 🔹 8. **Interop Support**

* COM Interop
* P/Invoke

---

## Why Are Some Components **Not in .NET Core**?

.NET Core (and later .NET 5/6/7/8) was **rewritten from scratch** with different design goals:

* **Cross-platform support**
* **Modularity**
* **Performance and scalability**
* **Cloud-readiness**
* **Simplified development**

So Microsoft **intentionally left out or redesigned** components that didn’t align with these goals.

---

## Components Not (or Initially Not) Included in .NET Core — And Why

| Component / Feature                | Included in .NET Core?        | Reason for Exclusion or Replacement                                                          |
| ---------------------------------- | ----------------------------- | -------------------------------------------------------------------------------------------- |
| **Web Forms (ASP.NET)**            | ❌ No                          | Tightly coupled to IIS and Windows UI model                                                  |
| **WCF (Windows Comm. Foundation)** | ❌ No                          | Complex, SOAP-heavy; replaced by gRPC, REST                                                  |
| **Windows Workflow (WF)**          | ❌ No                          | Limited usage, heavyweight, not cross-platform                                               |
| **System.Drawing (GDI+)**          | Partially (platform-specific) | Windows-only dependency, replaced by `System.Drawing.Common` then moved to `SkiaSharp`, etc. |
| **WinForms / WPF**                 | ✅ Yes (but Windows-only)      | Available in .NET Core 3.0+ but limited to Windows                                           |
| **Global Assembly Cache (GAC)**    | ❌ No                          | GAC caused versioning/deployment issues; replaced by NuGet/local deployment                  |
| **AppDomains**                     | ❌ No                          | Complex and unsafe isolation model; replaced by `AssemblyLoadContext`                        |
| **Code Access Security (CAS)**     | ❌ No                          | Obsolete; never worked well cross-platform                                                   |
| **Remoting**                       | ❌ No                          | Insecure, complicated, and obsolete; replaced by modern communication models                 |
| **Full Reflection.Emit**           | Partially                     | Reflection.Emit support is limited on non-Windows platforms                                  |
| **Enterprise Services (COM+)**     | ❌ No                          | Very Windows-specific; rarely used outside of legacy enterprise apps                         |

---

## What's Included in .NET Core / .NET 5+?

###  Always Included (Cross-platform):

* **CoreCLR** runtime
* **Base Class Libraries (BCL)**
* **ASP.NET Core**
* **Entity Framework Core**
* **gRPC, SignalR**
* **LINQ, Span<T>, Memory<T>**
* **Generic Host and Dependency Injection**
* **NuGet packaging**
* **System.Text.Json**
* **System.IO.Pipelines**
* **Self-contained deployment support**

### Windows-only in .NET Core:

* WinForms and WPF (starting in .NET Core 3.0)
* COM Interop
* System.DirectoryServices (partial support in .NET 7+)

---

## Example: WCF vs gRPC

Instead of using WCF, .NET Core pushes modern technologies:

### Old WCF:

```csharp
[ServiceContract]
public interface IMyService
{
    [OperationContract]
    string GetData(int value);
}
```

### Modern .NET Core (gRPC or REST):

```csharp
[ApiController]
[Route("api/[controller]")]
public class DataController : ControllerBase
{
    [HttpGet("{value}")]
    public string Get(int value) => $"Value: {value}";
}
```

Or with gRPC:

```protobuf
service DataService {
  rpc GetData (DataRequest) returns (DataReply);
}
```

---

## Modular Design with .NET Core

Instead of bundling everything, .NET Core uses **NuGet packages**:

```bash
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
dotnet add package Microsoft.AspNetCore.Authentication.JwtBearer
```

This modularity makes apps:

* Smaller
* More customizable
* Easier to update independently

---

## Summary

| .NET Framework                   | .NET Core / .NET 5+                      |
| -------------------------------- | ---------------------------------------- |
| Windows-only                     | Cross-platform                           |
| Monolithic (everything built-in) | Modular (install only what you need)     |
| GAC, Web Forms, WCF, WF          | NuGet, ASP.NET Core, gRPC                |
| Ideal for legacy enterprise      | Ideal for modern web/cloud/microservices |
| Slower evolution                 | Fast innovation & open-source            |


