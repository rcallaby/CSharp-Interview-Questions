# Question 8 - Design Patterns

## Can you explain the use of the builder pattern for constructing complex objects?

Yes, of course! The Builder pattern is a creational design pattern that provides a way to construct complex objects step by step. It's especially useful when the construction process is complex, and the resulting objects are expected to be different in some way. The Builder pattern allows the construction process to be separated from the object being constructed, making it easier to change the construction process or the object being constructed independently.

Here's how the Builder pattern works in C#:

Create a Builder interface that defines the steps required to build the complex object.
Create concrete builder classes that implement the Builder interface and provide a specific implementation for each step.
Create a Director class that knows how to construct the complex object using the Builder interface.
The client code creates an instance of the Director class, and passes in a specific concrete Builder instance to construct the desired object.

Here's an example of using the Builder pattern in C# to construct a sandwich:

```
interface ISandwichBuilder
{
    void AddBread();
    void AddMeat();
    void AddCheese();
    void AddVeggies();
    Sandwich GetSandwich();
}

class SandwichBuilder : ISandwichBuilder
{
    private Sandwich _sandwich;

    public SandwichBuilder()
    {
        _sandwich = new Sandwich();
    }

    public void AddBread()
    {
        _sandwich.Bread = "Whole Wheat";
    }

    public void AddMeat()
    {
        _sandwich.Meat = "Turkey";
    }

    public void AddCheese()
    {
        _sandwich.Cheese = "Cheddar";
    }

    public void AddVeggies()
    {
        _sandwich.Veggies = "Lettuce, Tomatoes, Onions";
    }

    public Sandwich GetSandwich()
    {
        return _sandwich;
    }
}

class Sandwich
{
    public string Bread { get; set; }
    public string Meat { get; set; }
    public string Cheese { get; set; }
    public string Veggies { get; set; }
}

class SandwichMaker
{
    private readonly ISandwichBuilder _builder;

    public SandwichMaker(ISandwichBuilder builder)
    {
        _builder = builder;
    }

    public void BuildSandwich()
    {
        _builder.AddBread();
        _builder.AddMeat();
        _builder.AddCheese();
        _builder.AddVeggies();
    }

    public Sandwich GetSandwich()
    {
        return _builder.GetSandwich();
    }
}

class Program
{
    static void Main(string[] args)
    {
        ISandwichBuilder builder = new SandwichBuilder();
        SandwichMaker maker = new SandwichMaker(builder);
        maker.BuildSandwich();
        Sandwich sandwich = maker.GetSandwich();

        Console.WriteLine("Bread: " + sandwich.Bread);
        Console.WriteLine("Meat: " + sandwich.Meat);
        Console.WriteLine("Cheese: " + sandwich.Cheese);
        Console.WriteLine("Veggies: " + sandwich.Veggies);

        Console.ReadLine();
    }
}

```

In this example, the SandwichBuilder class implements the ISandwichBuilder interface, providing a specific implementation for each step of building a sandwich. The SandwichMaker class uses the ISandwichBuilder interface to build a sandwich, and the client code creates an instance of the SandwichMaker class, passing in a SandwichBuilder instance to construct the desired sandwich object. This way, the construction process is separated from the object being constructed, making it easier to change the construction process or the object being constructed independently.

The Builder pattern provides a flexible way to construct complex objects by separating the construction process from the object being constructed. It's especially useful when the construction process is complex and the resulting objects are expected to be different in some way. By using the Builder pattern, you can change the construction process or the object being constructed without affecting the other parts of the code, making your code more maintainable and flexible.