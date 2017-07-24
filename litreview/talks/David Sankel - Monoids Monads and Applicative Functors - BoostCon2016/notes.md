# David Sankel: Monoids, Monads, and Applicative Functors: Repeated Software Patterns

https://youtu.be/DiisKQAkGM4

*A talk given at BoostCon/C++Now 2016*

***Abstract: Forget factories, singletons, and proxies; What are the real patterns in software development? This talk explores abstract mathematical structures that commonly recur in software development. Once a mind is trained to recognise these patterns, it becomes easy to identify the fundamental operations for domain specific classes and how to put the pieces together. This discussion is for those who enjoy math, abstract concepts, and expanding their minds.***

![ID](id-slide.jpg)



## [Why Functional Software Patterns?](https://youtu.be/DiisKQAkGM4?t=47s)


* In a nutshell: we want to figure out what should be the public members of classes:
  ```
  class Foo {
   public:
    // What goes here?
   private:
    // etc.
  };
  ```
> These are principals that are going to guide design.

* Answer Design Questions:
  * What are the "fundamental" operations?
  * What can the user do with the provided flexibility
  * How does this relate to other classes?


* Functional patterns are *not* for the user
  * User's don't recognise them. "What's a monadic bind operation?"
  * Code becomes less clear. Generic code is fun, but readable code is better.



## [A Bit of History](https://youtu.be/DiisKQAkGM4?t=2m21s)


* Haskell
  - Haskell was an academic programming language modelled from mathematical notation.
  - Purity is a big deal
  - Emphasis on purity (sans monads) made Haskell 1.0 a toy language for academics, because IO was stream based an clunky.


* Then monads hit the stage…
  - 1989—Eugenio Moggi uses monads to describe model states and exceptions.
  - 1992—Walder uses monads to express IO in Haskell.
  - Category Theory becomes popularised in functional programming.


* What is Category Theory?
  - Attempted to abstract over various mathematical domain (T.T. and connect topology and algebra)
  - In 1942, Eilenberg and Mac Lane, working on foundations.
  - Generality made it applicable to many domains, including music theory (T.T. which Hudak was a big fan of)
  - Category, Functor, Duality, Monad, Isomorphisms, …
  - All about widely repeated patterns.

> It's all about these widely repeated patterns. Patterns in nature.



## [Monoids](https://youtu.be/DiisKQAkGM4?t=6m22s)

[*Definition:*](https://youtu.be/DiisKQAkGM4?t=6m22s) A ***monoid*** is a type $T$ with binary operation $\oplus$ which combines its values.
* $\oplus$ mus be associative. That is, $(a \oplus b) \oplus c = a \oplus (b \oplus c)$.
* $T$ has a special value $e$ such that $e\oplus x = x\oplus e = x$ for all $x\in T$.

***NB(T.T.):*** Sankel uses the words "special value" or "empty" or "empty value" for the identity element. I'm going to use the term *identity element* in these notes because it is more familiar to me.


* Numeric types form monoids under addition (with $0\in N$ identity) and multiplication (with $1\in N$ identity).


* The unsigned type with `std::max(.,.)` with the 0 element as identity. T.T.
  - `max(max(a, b), c) == max(a, max(b, c))`
  - `max(0, x) = max(x, 0) = x` for all `x ∈ unsigned`.

***NB(T.T.):*** I'll use the standard notation (`unsigned`, `std::max`) from hereon.

* Monoids are all over the place. What is the identity value for (`float`, `std::min`)?
  - Identity value is `INFINITY` or `FLT_MAX`.


* (`std::vector<.>`, `append(⋅, ⋅)`). Where append `append : std::vector<T> -> std::vector<T> -> std::vector<T>` concatenates the vectors. In this case, the empty vector is the unity element. Here is Sankel's example implementation of `append`:
  ```
  template <typename T>
  std::vector<T> append(std::vector<T> lhs, std::vector<T> &rhs) {
    lhs.reserve(lhs.size() + rhs.size());
    lhs.insert(lhs.end(), rhs.begin(), rhs.end());
    return lhs;
  }
  ```
  NB(T.T.) Notice how `lhs` is passed in by copy. Nice.

  NB(T.T.) An alternative implementation might be
  ```
  template <typename T>
  std::vector<T> append(std::vector<T> lhs, std::vector<T> &rhs) {
    lhs.insert( lhs.end(), rhs.cbegin(), rhs.cend() );
    return lhs;
  }
  ```
  As pointed out [here](http://stackoverflow.com/a/2208316/1827360), unless the iterators are input iterators, the vector will figure out the required size and copy appended data at one go with linear complexity. This is guaranteed by the standard: item 23.2.4.4, where the complexity is specified to be linear in the number of elements in the range [first,last) plus the distance to the end of the vector.



## [Fancy Monoids](https://youtu.be/DiisKQAkGM4?t=11m22s)


* `The std::optional Template`
  - A `std::optional<t>` is either "null" (`std::nullopt`) or has a value of type `T`.
    ```
    std::optional<double> o = std::nullopt;
    // o is null, vis. `bool(o) == false'
    o = 3.0;
    // o has value 3.0, vis. `bool(o) == true' and `*o = 3.0'
    ```


* (T.T. My wording) If (`T`, $\oplus$) is a monoid, then so is (`std::optional<T>`, `append`) with the following morphism $\oplus\mapsto$`append`:
  ```
  // T.T. Why are we calling this append?
  std::optional<T> append(std::optional<T> lhs, std::optional<T> rhs) {
    if (!lhs)
      return rhs;
    else {
      if (rhs) // both sides non-empty
        return std::optional<T>(*lhs ⊕ *rhs);
      else
        return lhs;
    }
  }
  ```


* Another monoid can be formed from `std::optional<T>` on a monoid `T` with the operation:
  ```
  // T.T. Why are we calling this append?
  std::optional<T> append(std::optional<T> lhs, std::optional<T> rhs) {
    if (!lhs)
      return rhs;
    else {
      if (rhs)
        return rhs;
      else
        return lhs;
    }
  }
  ```


* Functions sharing a return type form a monoid with the following composition. For a monoid type `T`
  ```
  template<typename T, typename A> // Added by T.T.
  std::function<T(A)> append(std::function<T(A)> lhs, std::function<T(A)> rhs) {
    return [lhs, rhs](A a) { return lhs(a) ⊕ rhs(a); }
  ```
  with identity
  ```
  const std::function<T(A)> identity_element = []() {
    return T::identityElement;
  };
  ```


* Search for the `n` best occurrences of a word within a million documents
  - Key insight: an n-heap is a monoid
  - Split documents between cluster nodes.
  - send word to each cluster node.
  - Each cluster node generates a heap using parallelisation.
  - Each cluster node sends its heap to a collection node.
  - The collection node joins the heaps.
> An n-heap keeps the best elements in order of their bestness.


* Monoids:
  - Scale very well. (Operations can be distributed because of associativeity)
  - Monoids compose via functions, optional and other things.
  - Monoids are common.



## [Functors](https://youtu.be/DiisKQAkGM4?t=19m25s)


*[Definition:](https://youtu.be/DiisKQAkGM4?t=19m25s)* A ***functor*** is a class template (`Functor<T>`) with a single template parameter and a callable (map) which has the following properties:
* `map(f, a)` is a legal expression when:
  - `a` is a value of type `Functor<T>` for some type `T`.
  - `f` is a callable that accepts a single argument of type `T`.
  - Let `U` be the return type of `f(t)` for `t`$\in$`T`. The result of `map(f, a)` is type `Functor<U>`
* If `f(t) == t` for all `t`$\in$`T`, then `map(f, a) == a` for all values of type `Functor<T>`.
* `map(g, map(f, a)) = map( f, a)`, where
  ```
  auto gf = [f, g](auto t) { return g(f(t)); }
  ```

* *Intuititon:* Functors are like containers, or wrappers for value(s). The map function opens up the values in the container, applies the specified operation, and wraps the return value in the container.

NB(T.T.) I'm not comfortable with this description yet. I think it's too specific and looses a lot of what the word functor means in Category Theory. In Category Theory, it's the morphism between categories that is called the functor. Not the object in the codomain!

***NB(T.T.)*** If a monoid is a category with only a single formal object, and the elements of the monoid are the arrows with compositions, then the functor need only be the transformation on the morphisms. Then you get something like this `map` picture of functors. I need to think about that more. But that would mean the functor needs to preserve the composition of the monoids, which is to say that it has to preserve the binary operation. So, the argument to map is actually a monoid!


* `std::vector` is a functor with the map operation:
  ```
  template <typename T, typename U>
  std::vector<U> map(const std::function < U(T) & f, const std::vector<T> &a) {
    std::vector<U> result;
    for (const T &t : a)
      result.push_back(f(t));
    return result;
  }
  ```
NB(T.T.): I think reserving the space for the result up front would be better than pushing back and constantly having to reallocate.

NB(T.T.) Passing `std::functions` are inefficient. Perhaps passing as a template parameter?


* Missing slide: the online notes have an additional slide called "A more efficient map" with only this code block:
```
template <typename T, typename F> auto map(F f, const std::vector<T> &a) {
  std::vector<std::result_of_t<F(T)>> result;
  for (const T &t : a)
    result.push_back(f(t));
  return result;
}
```


* An example for `std::optional<T>` functor:
  ```
  template <typename T, typename U>
  std::optional<U> map(std::function<U(T)> f, std::optional<T> a) {
    if (a)
      return std::optional<U>(f(*s));
    else
      return std::nullopt;
  ```

* `std::set` is a functor under the additional constraint that functions passed to `map` must return ordered types. (If you screw with order, then you bugger the identity property.) There was some controversy (or discussion) about whether or not this constraint is sufficient.


* `std::pair` isn't a functor unless one of the template parameters is fixed.
  ```
  template <typename A, typename T, typename U>
  std::pair<A, U> map(std::function<U(T)> f, std::pair<A, T> a) {
    return std::make_pair(a.first, f(a.second));
  }
  ```
  This will be important to me when constructing behaviours (signal types). We can fix the time-stamp type.


* `std::function` is a functor if you fix the parameters. The map builds a new function which transforms the result of the old one.
  ```
  template <typename A, typename B, typename C>
  std::function<C(A)> map(std::function<C(B)> f, std::function<B(A)> g) {
    return [f, g](A x) { return f(g(x)); };
  }
  ```
  NB(T.T.) This map returns the composition `f`$\circ$`g`.
  ```@mermaid
  graph LR;
  A --"std::function< B(A) > g"--> B;
  B --"std::function< C(B) > f"--> C;
  A --"f∘g"--> C;
  ```


* Cute example. To convert a vector of optional ints (`std::vector<std::optional<int>>`) into a vector of optional strings (`std::vector<std::optional<std::string>>`) unpack this way:
  ```
  std::vector<std::optional<std::string>>
  get_strings(const std::vector<std::optional<int>> &ints) {
    auto f1 = [](auto i) { return std::to_string(i) };
    auto f2 = [](auto o) { return map(f1, o); };
    auto f3 = [](auto v) { return map(f2, v); };
    return f3(ints);
  }
  ```
  NB(T.T.) This is a great example demonstrating the composability of functors, which is one of the axioms. I think I'll use this example in my talk. I would like to find a way to use a partial application. (Well, really the lambdas are partially applying the map functions. They're binding the first arguments.)



## [Applicative Functor](https://youtu.be/DiisKQAkGM4?t=31m12s)


*[Definition:](https://youtu.be/DiisKQAkGM4?t=31m12s)* an ***applicative functor*** (`Applicative<T>`) is a functor with two extra operators, `pure` and `apply`, which obey the following rules:
* `pure(T t)` results in a value of type `Applicative<T>`. (It packs `t` into the container type.)
* Let `aff` be shorthand for "applicative functor function", and `afv` shorthand for "applicative functor value". Then, `apply(aff, afv)` is a legal expression when:
  - `aff` has type `Applicative<F>` for some callable `F` where `f(T t)` is well defined if `f` is of type `F(T)`.
  - `afv` has type `Applicative<T>` for some type `T`.
  - `apply(aff, afv)` has type `Applicative<U>` iff `f(t)` returns a `U`.


* Applicative Functor Laws
  - If `f(t) == t` for all `t`, then `apply(pure(f), a) == a` for all `a`.
  - `apply(pure(f), pure(t)) == pure(f(t))` for all `f` and `t`.
  - `apply(a, pure(t)) == apply(pure(f), a)` when `f(g) == g(t)` for all `g`.
  - `apply(a, apply(b, c)) == apply(apply(apply(pure(f), a), b), c)` when `f(g, h)(t) == g(h(t))` for all `g`, `h`, and `t`.
  - `map(f, a) == apply(pure(f), a)`


* An applicative functor wraps a value into the container. The function `apply` applies a contained function to a contained value to get a contained result.


* For example, the `std::optional` applicative functor:
  - `pure(.)` is simply
    ```
    template <typename T> std::optional<T> pure(T t) { return std::optional<T>(t); }
    ```
  - `apply(., .)` is:
    ```
    template <typename T, typename U>
    std::optional<U> apply(std::optional<std::function<U(T)>> a,
                           std::optional<T> b) {
      if (a && b)
        return std::optional<U>( (*a)(*b) );
      else
        return std::nullopt;
    }
    ```
  - Applicative functor properties
    ```
    const std::optional<double> a = /* etc. */;
    const std::optional<double> b = /* etc. */;
    const std::optional<double> c = apply(std::plus<>(), a, b);
    const std::optional<double> d = apply(std::negate<>(), c);
    // plus<> and negate<> should be optional. Implicit conversion?
    ```
  - This propagates errors. If there is an error along the way, you wind up with a nullopt. For example,
    ```
    const double myValue = /* etc. */;
    const std::optional<Command> cmd = /* fetch command */; // maybe from srvr
    const std::optional<std::function<double(double)>> func =
        map(funcFromCommand, cmd);
    const std::optional<double> result = apply(func, pure(myValue));
    ```


* Is `std::vector` and applicative functor? You've got a vector of functions, `{f1, f2, ...}` and a vector of values `{t1,t2, ...}`. What can you do?
  - Map all functions to all arguments: `{f1(t1), f1(t2), ..., f2(t1), f2(t2, ...)}`
  - Example:
    ```
    const std::vector<double> a {1.0, 2.0, 3.0};
    const std::vector<double> b {10.0, 20.0, 30.0};
    const std::vector<double> c = apply(pure(std::plus<>()), a, b);
    ```
* Many different applicative functors:
  - std::future
  - continuations
  - exception-style errors
  - behaviors in functional reactive programming
  - parsers
  - etc.

## [Parser applicative functors]()

* *I'm going to neglect the parser example for now. It's interesting to watch, but not of enough interest to me at the moment to take notes.*

## [Review](https://youtu.be/DiisKQAkGM4?t=48m53s)
  - Monoids -> Highly parallel patterns ($\oplus$).
  - Functors -> Do things to stuff inside a wrapper. (`map` produces un/rewrapping versions of functions.)
  - Applicative functors -> Put stuff inside (`pure`). The stuff inside can do things to the stuff inside (`apply`).

## [Monads](https://youtu.be/DiisKQAkGM4?t=49m33s)

*[Definition:](https://youtu.be/DiisKQAkGM4?t=49m33s)* A ***monad*** (`Monad<T>`) is an applicative functor with an extra operation, `join(..)`, which obeys the following rule:
  - `join(Monad<Monad<T>> a)` returns a value of type `Monad<T>`.

* Monad laws: A bit more complex to express in C++.
  - Joining outside-in vs. inside-out shouldn't make a difference.
  - See https://en.wikibooks.org/wiki/Haskell/Category_theory


* Join for `std::optional`:
  ```
  template <typename T> std::optional<T> join(std::optional<std::optional<T>> a) {
    if (a)
      return *a;
    else
      return std::nullopt;
  }
  ```

* Other Monads:
  - `std::vector`
  - parser
  - functions with single parameter of type `A`.


* The monadic bind operation is defined in terms of the other operations. For a given Monad<T>:
  ```
  template <typename T, typename U>
  Monad<U> bind(Monad<T> m, std::function<Monad<U>(T)> f) {
    return join(apply(pure(f), m));
  }
  ```
  The monad bind operation is notated as an overload of shift: `a >> f`. I believe Haskell uses `>>=`.

* Example:
  ```
  std::optional<int> get_int();

  std::optional<int> result =
           get_int() >> [=](auto a) {
    return get_int() >> [=](auto b) {
    return get_int() >> [=](audo c) { return pure(a + b + c); }
    }
  }
  ```
  this looks like the imperative code:
  ```
  auto a = get_int();
  auto b = get_int();
  auto c = get_int();
  return a+b+c;
  ```

* This was a big deal for Haskell, because then it could handle impurity in a pure way? I/O is a monad, Haskell can do monads and so Haskell becomes more than a toy language.


* But, what do monads do for us?
  - Express different models of computation within C++.
    * std::vector gives a language with nondeterminism.
    * std::optional provides a language with error fallthrough.
    * Continuation language, etc.
  - Provide more control over computation.
    * Serialize and de-serialize computations.
    * Command pattern embedded language.
  - Imperative template metaprogramming.


* This is just the beginning. More interesting patterns:
  - Semigroup
  - Category
  - Arrow
  - Comonad


## [Question period](https://youtu.be/DiisKQAkGM4?t=1h4m47s)
