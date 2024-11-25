# Question 23 - Design Pattern

## How would you use design patterns to develop a simple to-do app?

### MVC Design Pattern Overview:
1. **Model**: Represents the data and business logic of the application (e.g., to-do items).
2. **View**: Responsible for displaying the user interface and data.
3. **Controller**: Acts as the intermediary between the Model and View, handling user input and updating the View.

### C# Example: Simple To-Do List App

#### 1. **Model** (`TodoItem.cs`):
The `TodoItem` class will represent each task in the to-do list.

```csharp
public class TodoItem
{
    public string Task { get; set; }
    public bool IsCompleted { get; set; }

    public TodoItem(string task)
    {
        Task = task;
        IsCompleted = false;
    }
}
```

#### 2. **Model** (`TodoList.cs`):
This class manages a collection of `TodoItem` objects.

```csharp
using System.Collections.Generic;

public class TodoList
{
    public List<TodoItem> Items { get; private set; }

    public TodoList()
    {
        Items = new List<TodoItem>();
    }

    public void AddTask(string task)
    {
        Items.Add(new TodoItem(task));
    }

    public void RemoveTask(string task)
    {
        var itemToRemove = Items.Find(item => item.Task == task);
        if (itemToRemove != null)
        {
            Items.Remove(itemToRemove);
        }
    }

    public void MarkTaskAsComplete(string task)
    {
        var item = Items.Find(item => item.Task == task);
        if (item != null)
        {
            item.IsCompleted = true;
        }
    }

    public List<TodoItem> GetAllTasks()
    {
        return Items;
    }
}
```

#### 3. **View** (`TodoView.cs`):
The `TodoView` class will be responsible for displaying the tasks.

```csharp
using System;
using System.Collections.Generic;

public class TodoView
{
    public void DisplayTasks(List<TodoItem> tasks)
    {
        Console.WriteLine("To-Do List:");
        foreach (var task in tasks)
        {
            string status = task.IsCompleted ? "[Completed]" : "[Pending]";
            Console.WriteLine($"{task.Task} {status}");
        }
    }

    public void GetTaskInput()
    {
        Console.WriteLine("Enter a new task: ");
    }

    public void AskForTaskToRemove()
    {
        Console.WriteLine("Enter the task you want to remove: ");
    }

    public void AskForTaskToComplete()
    {
        Console.WriteLine("Enter the task you want to mark as complete: ");
    }
}
```

#### 4. **Controller** (`TodoController.cs`):
The `TodoController` class handles user interaction and updates the model and view accordingly.

```csharp
using System;

public class TodoController
{
    private TodoList _todoList;
    private TodoView _todoView;

    public TodoController(TodoList todoList, TodoView todoView)
    {
        _todoList = todoList;
        _todoView = todoView;
    }

    public void AddTask()
    {
        _todoView.GetTaskInput();
        string task = Console.ReadLine();
        _todoList.AddTask(task);
    }

    public void RemoveTask()
    {
        _todoView.AskForTaskToRemove();
        string task = Console.ReadLine();
        _todoList.RemoveTask(task);
    }

    public void MarkTaskAsComplete()
    {
        _todoView.AskForTaskToComplete();
        string task = Console.ReadLine();
        _todoList.MarkTaskAsComplete(task);
    }

    public void DisplayTasks()
    {
        var tasks = _todoList.GetAllTasks();
        _todoView.DisplayTasks(tasks);
    }
}
```

#### 5. **Main Program** (`Program.cs`):
The `Program` class will initialize everything and simulate interaction with the to-do list.

```csharp
using System;

public class Program
{
    public static void Main(string[] args)
    {
        TodoList todoList = new TodoList();
        TodoView todoView = new TodoView();
        TodoController todoController = new TodoController(todoList, todoView);

        bool running = true;
        while (running)
        {
            Console.Clear();
            todoController.DisplayTasks();

            Console.WriteLine("\nOptions:");
            Console.WriteLine("1. Add Task");
            Console.WriteLine("2. Remove Task");
            Console.WriteLine("3. Mark Task as Completed");
            Console.WriteLine("4. Exit");
            Console.Write("Choose an option: ");
            string choice = Console.ReadLine();

            switch (choice)
            {
                case "1":
                    todoController.AddTask();
                    break;
                case "2":
                    todoController.RemoveTask();
                    break;
                case "3":
                    todoController.MarkTaskAsComplete();
                    break;
                case "4":
                    running = false;
                    break;
                default:
                    Console.WriteLine("Invalid option.");
                    break;
            }
        }
    }
}
```

### Key Concepts in the Code:
- **Model**: Handles the data (the `TodoItem` and `TodoList` classes).
- **View**: Displays data to the user (the `TodoView` class).
- **Controller**: Coordinates the actions between the model and view (the `TodoController` class).

### How It Works:
- The `Program` class runs the application, where the user can interact with the to-do list by adding, removing, or completing tasks.
- The `TodoController` manages user input and modifies the `TodoList` model.
- The `TodoView` displays the current state of the to-do list and prompts for user input.

### Running the Application:
When you run the application, it will show the current list of tasks and prompt you to choose an action (add a task, remove a task, mark a task as completed, or exit). You can add, remove, and complete tasks as you wish.

This is a basic implementation of the MVC design pattern in a C# console application. It is easy to expand and modify based on additional requirements, such as saving tasks to a file or adding more advanced features like due dates or priorities.