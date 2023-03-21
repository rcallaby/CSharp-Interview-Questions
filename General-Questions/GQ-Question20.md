# Question 20 - General Questions

## Can you explain the difference between lazy and eager evaluation in C#?

In C#, lazy evaluation and eager evaluation refer to two different approaches for evaluating expressions and handling computations.

Lazy evaluation, also known as delayed evaluation, is an evaluation strategy where expressions are not evaluated until they are actually needed. This means that the computation is deferred until it is absolutely necessary, usually to avoid unnecessary calculations or to save resources. In C#, lazy evaluation is often implemented using a technique called "lazy loading," where the value of an expression is only computed the first time it is needed, and then cached for later use. Lazy evaluation can be useful when working with complex, resource-intensive calculations or when working with large data sets that may not all be needed at once.

On the other hand, eager evaluation, also known as immediate evaluation, is the default evaluation strategy in C#. This means that expressions are evaluated as soon as they are encountered in the code, without any delay. This can be useful for simple or short-lived computations where the result is needed immediately, but it can also lead to unnecessary computation or resource consumption if the expressions are not carefully designed.

To illustrate the difference between the two approaches, consider the following example:

```
int x = 5;
int y = 10;
int sum = x + y; // eager evaluation, sum is computed immediately

```
In this example, the expression x + y is evaluated immediately when it is encountered in the code, and the result is stored in the variable sum. This is an example of eager evaluation.

In contrast, consider the following example:

```
Func<int> lazySum = () => x + y; // lazy evaluation, sum is not computed yet
int result = lazySum(); // the expression is evaluated when it is needed

```
In this example, a Func<int> delegate is created that represents the expression x + y. However, the expression is not actually evaluated until the delegate is called with lazySum(). This is an example of lazy evaluation, where the computation is deferred until it is actually needed.

Overall, both lazy and eager evaluation have their own strengths and weaknesses, and the choice between the two depends on the specific requirements and constraints of the problem at hand.