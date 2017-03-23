# Functional Thinking with Neal Ford

https://youtu.be/JeK979aqqqc

***Neal Ford breaks down the concepts behind functional programming in this video from JaxConf 2012.***

NB(T.T.) A good soft introduction with material I cam use in talks and chapter intros.


* FP is from academic languages that are merging into the mainstream.

* In the .net world, F# now ships as a first-class citizen with Visual Studio.

* Quote from Michael Feathers, author of "Working with Legacy Code":
  > OO makes code understandable by encapsulating moving parts. FP makes code understandable by minimizing moving parts.

* > If there is no internal state, there is no compelling reason to make things private. In fact, there's some real nice benefits to making methods public.

* NB(T.T.) Interesting idea: people would still use classes to group behaviours that *go together*. In a functional construction, could namespaces fill that need?

* > In the Java world, we often don't think of re-usability at the function or method levels because it's been so beaten into use that re-usability always happens at the class level.

  -- https://youtu.be/JeK979aqqqc?t=14m13s

* Recursion can be a mechanism for eliminating state. It can eliminate iteration variables.

* Strict evaluation? Wikipedia:
  > Under Church encoding, eager evaluation of operators maps to strict evaluation of functions[further explanation needed]; for this reason, strict evaluation is sometimes called "eager".

  and

  > In computer programming, eager evaluation or greedy evaluation is the evaluation strategy used by most traditional programming languages. In eager evaluation, an expression is evaluated as soon as it is bound to a variable. An alternative to eager evaluation is lazy evaluation, where expressions are evaluated only when a dependent expression is evaluated.

* > All the Command Design Pattern is, is a band-aid for the fact that Java doesn't have a way to pass around code.

  -- https://youtu.be/JeK979aqqqc?t=18m27s

* A point well made: as languages evolve, we're passing more and more busywork down to the language and runtime features. https://youtu.be/JeK979aqqqc?t=22m49s

* I like [this example](https://youtu.be/JeK979aqqqc?t=28m39s) to demonstrate functional syntax. (Will probably borrow.) I think a point can be driven home by adding to
  ```
  (defn sum-factors [number]
    (reduce + (factors number)))
  ```
  the statement that you can read the function body as
  ```
    reduce( (+), factors(number));
  ```
  in C++ or Java. The more familiar placement of parens makes it clear that the operator is the handle for the sum operation. Someone not familiar with functional languages reads `(reduce + (factors number))` as trying to add the value of `reduce` to what-ever-the-hell `(factors number)` is.
