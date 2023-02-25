# Question 11 - General Questions

## Can you explain the use of the "this" keyword in C#?

In C#, the "this" keyword is a reference to the current instance of a class or struct. It is commonly used to:

Distinguish between instance variables and local variables with the same name: When a local variable has the same name as an instance variable, using "this" allows you to refer to the instance variable. For example:

```
class MyClass {
   int num;

   public void SetNum(int num) {
      this.num = num; // use "this" to refer to the instance variable
   }
}

```
Pass the current object as an argument to another method or constructor: You can use "this" to pass the current object as an argument to another method or constructor. For example:

```
class MyClass {
   int num;

   public MyClass(int num) {
      this.num = num; // pass "this" as an argument to set the instance variable
   }

   public void DoSomething() {
      OtherClass.Method(this); // pass "this" as an argument to another method
   }
}

```
Return the current object from a method: You can use "this" to return the current object from a method. This is useful for chaining method calls. For example:

```
class MyClass {
   public MyClass DoSomething() {
      // do something
      return this; // return the current object
   }

   public MyClass DoSomethingElse() {
      // do something else
      return this; // return the current object
   }
}

```
Overall, the "this" keyword is used to refer to the current object and is useful for disambiguating variables, passing the current object as an argument, and chaining method calls.