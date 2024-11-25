# Question 22 = Design Patterns

## How would you use design patterns to create a shopping cart?

Below you will find a very simplified version of how to implement a simple blockchain using C#. Of course, there are many more open source examples you can use to learn from but this is one of the more simplistic versions mainly used to help study for a technical interview.

### 1. **Strategy Pattern** - For Discount Strategies
The **Strategy** pattern allows us to define different discount strategies and apply them to the shopping cart dynamically. This is useful because the type of discount (e.g., seasonal discount, bulk discount, or coupon-based discount) may change depending on user inputs or conditions.

#### Example of Strategy Pattern:
```csharp
// Define an interface for the discount strategy
public interface IDiscountStrategy
{
    decimal ApplyDiscount(decimal totalAmount);
}

// Concrete strategy for no discount
public class NoDiscount : IDiscountStrategy
{
    public decimal ApplyDiscount(decimal totalAmount)
    {
        return totalAmount; // No discount
    }
}

// Concrete strategy for percentage-based discount
public class PercentageDiscount : IDiscountStrategy
{
    private decimal _percentage;
    public PercentageDiscount(decimal percentage)
    {
        _percentage = percentage;
    }

    public decimal ApplyDiscount(decimal totalAmount)
    {
        return totalAmount * (1 - _percentage / 100);
    }
}

// Concrete strategy for fixed amount discount
public class FixedDiscount : IDiscountStrategy
{
    private decimal _discountAmount;
    public FixedDiscount(decimal discountAmount)
    {
        _discountAmount = discountAmount;
    }

    public decimal ApplyDiscount(decimal totalAmount)
    {
        return totalAmount - _discountAmount;
    }
}
```

### 2. **Observer Pattern** - For Cart Updates
The **Observer** pattern allows us to notify other components (e.g., UI, inventory, or pricing systems) when the shopping cart’s state changes. This is ideal for updating the total amount, notifying users about cart changes, or adjusting prices dynamically based on cart content.

#### Example of Observer Pattern:
```csharp
// Subject (ShoppingCart)
public class ShoppingCart
{
    private List<IObserver> _observers = new List<IObserver>();
    private List<Item> _items = new List<Item>();

    public void Attach(IObserver observer)
    {
        _observers.Add(observer);
    }

    public void Detach(IObserver observer)
    {
        _observers.Remove(observer);
    }

    public void Notify()
    {
        foreach (var observer in _observers)
        {
            observer.Update(this);
        }
    }

    public void AddItem(Item item)
    {
        _items.Add(item);
        Notify(); // Notify observers when items are added
    }

    public decimal GetTotal()
    {
        return _items.Sum(item => item.Price);
    }
}

// Observer interface
public interface IObserver
{
    void Update(ShoppingCart shoppingCart);
}

// Concrete observer for updating UI
public class CartTotalObserver : IObserver
{
    public void Update(ShoppingCart shoppingCart)
    {
        Console.WriteLine($"Cart total updated: {shoppingCart.GetTotal()}");
    }
}
```

### 3. **Decorator Pattern** - For Additional Features (Gift Wrapping, Special Handling)
The **Decorator** pattern can be used to dynamically add responsibilities to the shopping cart, such as gift wrapping or special handling (e.g., express shipping).

#### Example of Decorator Pattern:
```csharp
// Abstract Component
public abstract class Cart
{
    public abstract decimal GetTotal();
}

// Concrete Component
public class BasicCart : Cart
{
    private List<Item> _items = new List<Item>();

    public void AddItem(Item item)
    {
        _items.Add(item);
    }

    public override decimal GetTotal()
    {
        return _items.Sum(item => item.Price);
    }
}

// Decorator
public abstract class CartDecorator : Cart
{
    protected Cart _cart;
    public CartDecorator(Cart cart)
    {
        _cart = cart;
    }

    public override decimal GetTotal()
    {
        return _cart.GetTotal();
    }
}

// Concrete Decorator for Gift Wrapping
public class GiftWrapDecorator : CartDecorator
{
    public GiftWrapDecorator(Cart cart) : base(cart) {}

    public override decimal GetTotal()
    {
        return base.GetTotal() + 5.00m; // Add gift wrap fee
    }
}

// Concrete Decorator for Special Handling
public class SpecialHandlingDecorator : CartDecorator
{
    public SpecialHandlingDecorator(Cart cart) : base(cart) {}

    public override decimal GetTotal()
    {
        return base.GetTotal() + 10.00m; // Add special handling fee
    }
}
```

### Putting it All Together:
Here’s how you can use the Strategy, Observer, and Decorator patterns together in a shopping cart.

```csharp
public class ShoppingCartExample
{
    public static void Main(string[] args)
    {
        // Create a basic shopping cart and add items
        var cart = new BasicCart();
        cart.AddItem(new Item("Item1", 50.00m));
        cart.AddItem(new Item("Item2", 30.00m));

        // Add observers
        var cartObserver = new CartTotalObserver();
        var shoppingCart = new ShoppingCart();
        shoppingCart.Attach(cartObserver);
        shoppingCart.AddItem(new Item("Item1", 50.00m));

        // Apply a discount strategy
        IDiscountStrategy discountStrategy = new PercentageDiscount(10);
        decimal totalWithDiscount = discountStrategy.ApplyDiscount(cart.GetTotal());

        Console.WriteLine($"Total after discount: {totalWithDiscount}");

        // Add decorators (gift wrap, special handling)
        Cart decoratedCart = new GiftWrapDecorator(new SpecialHandlingDecorator(cart));
        Console.WriteLine($"Total with decorators: {decoratedCart.GetTotal()}");
    }
}
```

### Summary:
1. **Strategy**: We use the Strategy pattern to choose the appropriate discount strategy dynamically.
2. **Observer**: We use the Observer pattern to notify other components (like UI or pricing systems) when the cart changes.
3. **Decorator**: We use the Decorator pattern to add features (such as gift wrapping or special handling) to the shopping cart without altering the original cart class.

This design is highly extensible and easily maintainable, allowing for new features (like additional discounts, payment methods, or services) to be added with minimal changes to the existing code.