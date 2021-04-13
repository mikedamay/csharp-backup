# About Lambdas

Like C# methods (and local functions) `lambda expressions` and their close cousins `delegates` allow program behavior to be specified.
Lambdas (and delegates) serve a slightly different goal to that of methods.
Whereas the call to a method entails both choice of behavior, determined by the method name/signature, and timing which depends on the position of the call within the control flow, in the case of lambdas the selection of the behavior can be separated from the timing.
Note that polymorphism can also be used to engineer this separation but at a much more coarse grained level and in a more verbose fashion.

The lambda feature is most easily seen to advantage in the case of operations on collections.
For example operations on a `List<T>` can be delegated to a `ForEach` method.  A lambda can be passed into the method and it will be applied to each item in the collection.
This is typically leveraged by selecting lambdas with different behaviors.  For example one choice might be to square every integer in the list and another might convert every integer to its absolute value.
A whole range of behavior can be added to `List<T>` or many other collections with an economy of effort and code.
The more declarative nature of the construct allows the code to be reasoned about more easily.

You are not restricted to using lambdas with standard (or third party) libraries.
You can use them with your own objects.

The uses you find for lambdas are fairly unlimited.
To mention a few, besides their use with collections, they are often used as callbacks or as inputs to frameworks and libraries.

## Syntax

The type of a lambda is provided by the declaration of a delegate.
A delegate has the form of a function signature.
For instance:
```csharp
private delegate int BinOp(int a, int b);
```
This is then used as the type of a variable or parameter.
For instance:
```csharp
private int Calculate(BinOp binOp)
{
    var val1 = GetVal1FromSomewhere();
    var val2 = GetVal2FromSomewhere();
    int result = BinOp(val1, val2);
    return TransformResultInSomeWay(result);
}
```
In our example, by passing in different binary operations at different times we can add considerable flexibility to the `Calculate()` method.

The easiest lambda syntax to understand to begin with a verbose form that looks like a function declaration.
For instance:
```csharp
BinOp add = (int a, int b)
{
    return a + b;
}
Calculate(add);
```

This can be refined to a format you will most often see in code, dropping the type names and the braces and introducing the `=>` operator.
So:
```csharp
BinOp subtract (a, b) => a - b;
Calculate(subtract);
```

A novel (and unique) feature of the lambda