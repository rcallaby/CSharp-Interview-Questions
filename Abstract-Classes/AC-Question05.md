# Question 5 - Abstract Classes

## Can you explain the SOLID principle of Single Responsibility and how it relates to abstract classes in C#?

The SOLID principles are a set of five design principles that aim to create well-structured, maintainable, and scalable software systems. The first principle, known as the Single Responsibility Principle (SRP), states that a class should have only one reason to change. In other words, a class should have only one primary responsibility.

This principle encourages you to design your classes in such a way that each class is focused on doing one thing and doing it well. This improves the maintainability of your code because changes related to a specific responsibility won't affect other parts of the code that are unrelated.

Now, let's relate the Single Responsibility Principle to abstract classes in C# using an example.

Suppose we're building a simple drawing application. We might have various shapes like circles, rectangles, and triangles. We want to apply the Single Responsibility Principle to our design.

Here's an example of how we might design our classes without adhering to SRP:

```
// This class violates SRP by having multiple responsibilities
class Shape
{
    public virtual void Draw() { /* Draw the shape */ }
    public virtual void Move() { /* Move the shape */ }
    public virtual void Resize() { /* Resize the shape */ }
}

```
In this example, the Shape class has multiple responsibilities: drawing, moving, and resizing. If any of these responsibilities changes, it could potentially impact the other responsibilities. This violates the SRP.

To adhere to the Single Responsibility Principle, we should separate these responsibilities into different classes. Abstract classes can be used to define common behavior that multiple classes share, while still adhering to SRP. Here's an improved design:

```
// Abstract class for drawing shapes
abstract class Shape
{
    public abstract void Draw();
}

// Separate class for moving shapes
class MovableShape : Shape
{
    public override void Draw() { /* Draw the shape */ }
    public void Move() { /* Move the shape */ }
}

// Separate class for resizing shapes
class ResizableShape : Shape
{
    public override void Draw() { /* Draw the shape */ }
    public void Resize() { /* Resize the shape */ }
}

```
In this design, we have separated the responsibilities of drawing, moving, and resizing into different classes. Each class adheres to the SRP, as they have only one primary responsibility.

By using abstract classes, we define a common interface (in this case, the Draw method) for the various shape-related classes. This allows us to ensure consistent behavior across different shapes while still adhering to the principle of single responsibility.

Remember, the Single Responsibility Principle helps create more maintainable code by reducing the impact of changes and improving the clarity of class responsibilities.
