# Question 4 - LINQ

## How can LINQ be used to perform grouping and aggregation operations on data?

LINQ (Language Integrated Query) is a powerful feature in C# that allows you to perform various operations on data in a concise and expressive way. Grouping and aggregation operations are commonly used to organize and summarize data. LINQ provides several methods to perform these operations.

## Grouping Data
The GroupBy method in LINQ can be used to group data based on one or more properties. For example, consider a collection of objects representing products:

```
var products = new List<Product>
{
    new Product { Name = "Product1", Category = "Category1", Price = 10.00m },
    new Product { Name = "Product2", Category = "Category2", Price = 20.00m },
    new Product { Name = "Product3", Category = "Category1", Price = 30.00m },
    new Product { Name = "Product4", Category = "Category2", Price = 40.00m },
    new Product { Name = "Product5", Category = "Category1", Price = 50.00m }
};

```
To group the products by category, you can use the GroupBy method as follows:

```
var productsByCategory = products.GroupBy(p => p.Category);

```
This will create an IEnumerable<IGrouping<string, Product>> where each grouping represents a unique category and contains all products belonging to that category. You can then iterate over the groupings and their associated products:

```
foreach (var group in productsByCategory)
{
    Console.WriteLine(group.Key); // Category name
    foreach (var product in group)
    {
        Console.WriteLine($"\t{product.Name} ({product.Price:C})");
    }
}

```
This will output:

```
Category1
    Product1 ($10.00)
    Product3 ($30.00)
    Product5 ($50.00)
Category2
    Product2 ($20.00)
    Product4 ($40.00)
```

## Aggregating Data
Aggregation functions such as Sum, Min, Max, Average, and Count can be used to calculate summary information for a group of data. For example, to calculate the total price of all products in each category, you can use the Sum method within a GroupBy operation:

```
var totalPricesByCategory = products
    .GroupBy(p => p.Category)
    .Select(g => new { Category = g.Key, TotalPrice = g.Sum(p => p.Price) });

```
This will create an IEnumerable of anonymous objects with two properties: Category (the category name) and TotalPrice (the sum of all prices for products in that category). You can then iterate over the results and display the summary information:

```
foreach (var item in totalPricesByCategory)
{
    Console.WriteLine($"{item.Category}: {item.TotalPrice:C}");
}

```
This will output:

```
Category1: $90.00
Category2: $60.00

```
There are many other aggregation functions available in LINQ, and they can be combined with grouping operations to perform complex calculations on data.

