# David Sankel: Monoids, Monads, and Applicative Functors: Repeated Software Patterns

https://youtu.be/DiisKQAkGM4

*A talk given at BoostCon 2016*

***Abstract: Forget factories, singletons, and proxies; What are the real patterns in software development? This talk explores abstract mathematical structures that commonly recur in software development. Once a mind is trained to recognise these patterns, it becomes easy to identify the fundamental operations for domain specific classes and how to put the pieces together. This discussion is for those who enjoy math, abstract concepts, and expanding their minds.***

![ID](id-slide.jpg)

* Haskell was an academic programming language modelled from mathematical notation.

* Applying the theory of _monads_ to Haskell allowed safe I/O side effects, making Haskell into a generally useful language rather than an academic toy model.

* **Definition:** a **monoid** is abstract set, T, with a binary operation, $\bigoplus$, that closes the set, is associative, and has an identity element in the set.

* Numerical types form monoids under addition (with $0\in N$ identity) and multiplication (with $1\in N$ identity).

* The unsigned type with `std::max(.,.)` with the 0 element as identity.

* The `std::vector<.>` type forms a monoid under `append() -> std::vector<T> -> std::vector<T> -> std::vector<T>` with the empty vector as a unity element.

* *Important:* `std::optional<SomeMonoid>` is a monoid under the operation of SomeMonoid:
  ```
  std::optional<SomeMonoid> append(std::optional<SomeMonoid> lhs,
                                   std::optional<SomeMonoid> rhs) {
    if (!lhs)
      return rhs;
    else {
      if (rhs) // both sides non-empty
        return std::optional<SomeMonoid>(*lhs ⨁ *rhs);
      else
        return lhs;
    }
  }
  ```

* Functions sharing a return type form a monoid:
  ```
  std::function<SomeMonoid(A)> append(std::function<SomeMonoid(A)> lhs,
                                      std::function<SomeMonoid(A)> rhs) {
    return [lhs, rhs](A a) { return lhs(a) $\bigoplus$ rhs(a); }
  ```
  with identity
  ```
  const std::function<SomeMonoid(A)> identity_element = []() {
    return SomeMonoid::identityElement;
  };
  ```

* **Definition:** In terms of C++, a ***monad*** is a class template (Functor<T>) with a single template parameter and a callable (map) which have the following properties:
  - `map(f, a)` is a legal expression when:
    - `a` is a value of type `Functor<T>` for some type `T`.
    - `f` is a callable that accepts a single argument of type `T`.
    - Let `U` be the return type of `f(T t)` The result of `map(f, a)` is type `Functor<U>`
  - If `f(t) == t` for all `t` of type `T`, then `map(f, a) == a` for all values of type `Functor<T>`.
  - `map(g, map(f, a)) = map( f, a)`, where `auto gf = [f,g](auto t){return g(f(t));}`.

* I think Sankel's `map()` should be `fmap()` for consistency.

* Functors are containers, or wrappers for value(s). For example, `std::optional<T>` is a functor. Also, `std::vector<T>` is a functor. The map function unwraps the internal value, applies the function, and wraps the result.

* An example for `std::optional<T>`:
  ```
  template <typename T, typename U>
  std::optional<U> fmap(std::function<U(T)> f, std::optional<T> a) {
    if (a)
      return std::optional<U>(f(*s));
    else
      return std::nullopt;
  ```
* `std::set` is a functor under the additional constraint that functions passed to `fmap` must return ordered types.

* `std::pair` isn't a functor unless one of the template parameters is fixed. This will be important to me when constructing behaviours. We can fix the time-stamp type.
  ```
  template <typename A, typename T, typename U>
  std::pair<A, U> fmap(std::function<U(T)> f, std::pair<A, T> a) {
    return std::make_pair(a.first, f(a.second));
  }
  ```

* `std::function` is a functor if you fix the parameters. The map builds a new function which transforms the result of the old one. Apparently this is just function composition.
  ```
  template <typename P, typename T, typename U>
  std::function<U(P)> fmap(std::function<U(T)> f, std::function<T(P)> g) {
    return [f, a](P p) { return f(g(p)); };
  }
  ```

* Cute example. To convert a vector of optional ints (`std::vector<std::optional<int>>`) into a vector of optional strings (`std::vector<std::optional<std::string>>`) unpack this way:
  ```
  std::vector<std::optional<std::string>>
  get_strings(const std::vector<std::optional<int>> &ints) {
    auto f1 = [](auto i) { return std::to_string(i) };
    auto f2 = [](auto o) { return fmap(f1, o); };
    auto f3 = [](auto v) { return fmap(f2, v); };
    return f3(ints);
  }
  ```

* **Definition:** an ***applicative functor*** is a functor with two extra operators, `pure` and `apply`, which obey the following rules:
  - `pure(T t)` results in a value of type `Applicative<T>`. (It packs `t` into the container type.)
  - Let `aff` be shorthand for "applicative functor function", and `afv` shorthand for "applicative functor value". Then, `apply(aff, afv)` is a legal expression when:
    - `aff` has type `Applicative<F>` for some callable `F` where `f(T t)` is well defined if `f` is of type `F(T)`.
    - `afv` has type `Applicative<T>` for some type `T`.
    - `apply(aff, afv)` has type `Applicative<U>` iff `f(t)` returns a `U`.

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

* Behaviours in FRP are functors. https://youtu.be/DiisKQAkGM4?t=37m44s

* Nice summary at [49m23s](https://youtu.be/DiisKQAkGM4?t=49m23s).
  - Monoids -> Highly parallel patterns ($\bigoplus$).
  - Functors -> Do things to stuff inside a wrapper. (`fmap` produces un/rewrapping versions of functions.)
  - Applicative functors -> Put stuff inside (`pure`). The stuff inside can do things to the stuff inside (`apply`).

* **Definition:** A ***monad*** (`Monad<T>`) is an applicative functor with an extra operation, `join(..)`, which obeys the following rule:
  - `join(Monad<Monad<T>> a)` returns a value of type `Monad<T>`.

* Monad bind operation (`a >> f`):
  ```
  template <typename T, typename U>
  Monad<U> bind(Monad<T> a, std::function<Monad<U>(T)> f) {
    return join(apply(pure(f), a))
  }
  ```

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

* This was a big deal for Haskell, because then it could handle inpurity in a pure way? I/O is a monad, Haskell can do monads and so Haskell becomes more than a toy language.

## Question period
