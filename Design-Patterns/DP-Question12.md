# Question 12 - Design Patterns

## Can you give an example of how to implement the Composite pattern in C# for creating a tree-like structure?

The composite pattern is a structural design pattern that allows you to build structures of objects in the form of a tree. The key idea is to have a single component interface that can represent both simple and complex components, and to define a composite component that contains child components. Here's a simple implementation of the composite pattern in C#:

```
using System.Collections.Generic;

interface IComponent
{
    void Add(IComponent component);
    void Remove(IComponent component);
    IComponent GetChild(int index);
    string Operation();
}

class Leaf : IComponent
{
    private string _name;

    public Leaf(string name)
    {
        _name = name;
    }

    public void Add(IComponent component)
    {
        // Leaves do not have children so this method is not implemented
    }

    public void Remove(IComponent component)
    {
        // Leaves do not have children so this method is not implemented
    }

    public IComponent GetChild(int index)
    {
        // Leaves do not have children so this method is not implemented
        return null;
    }

    public string Operation()
    {
        return _name;
    }
}

class Composite : IComponent
{
    private List<IComponent> _children = new List<IComponent>();

    public void Add(IComponent component)
    {
        _children.Add(component);
    }

    public void Remove(IComponent component)
    {
        _children.Remove(component);
    }

    public IComponent GetChild(int index)
    {
        return _children[index];
    }

    public string Operation()
    {
        int i = 0;
        string result = "Branch(";

        foreach (IComponent component in _children)
        {
            result += component.Operation();
            if (i != _children.Count - 1)
            {
                result += "+";
            }
            i++;
        }

        return result + ")";
    }
}

```
You can use this implementation to build a tree structure of objects. For example:

```
class Program
{
    static void Main(string[] args)
    {
        // Initialize a composite structure
        Composite root = new Composite();
        root.Add(new Leaf("Leaf A"));
        root.Add(new Leaf("Leaf B"));

        Composite comp = new Composite();
        comp.Add(new Leaf("Leaf C"));
        comp.Add(new Leaf("Leaf D"));

        root.Add(comp);
        root.Add(new Leaf("Leaf E"));

        // Display the whole tree
        Console.WriteLine("Whole tree structure:");
        Console.WriteLine(root.Operation());
    }
}

```
