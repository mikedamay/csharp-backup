# About Lambdas

Like C# methods (and local functions) `lambda expressions` and their close cousins `delegates` allow program behavior to be specified.
Lambdas (and delegates) serve a slightly different goal to methods.
Whereas the call to a method entails both choice of behavior, determined by the method name, and timing which depends on the position of the call within the control flow, in the case of lambdas the selection of the behavior can be separated from the timing.

The lambda feature is most easily seen to advantage in the case of operations on collections.
For example operations on a `List<T>` can be delegated to a `ForEach` method.  A lambda can be passed into the method and it will be applied to each item in the collection.
This is typically leveraged by selecting lambdas with different behaviors.
A whole range of behavior can be added to `List<T>` with an economy of effort and code.
The more declarative nature of the construct allows the code to be reasoned about more easily.


## Syntax




Note on polymorphism.  A more coarse grained approach.