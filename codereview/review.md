# Items for code review

## [Functional Template Library](https://github.com/beark/ftl)—C++ template library for fans of functional programming

## [Dobiasd/FunctionalPlus](https://github.com/Dobiasd/FunctionalPlus)—helps you write concise and readable C++ code.

This library is associated with a [udemy course](https://www.udemy.com/functional-programming-using-cpp/) that has two [YouTube videos](https://www.youtube.com/watch?v=jD8Tu1tqvZo) available for preview. I haven't taken the course, but this library is publicly available.

Features on review:
  * Function composition
  * Currying
  * Function traits
  * Intermediate value elision in the `fwd` namespace. (Is it lazy?)

### Function composition



### Currying
The library contains no general currying facilities. The `curry.hpp` header file contains *macro functions* which produce hard coded, nested lambdas for currying functions of up to 5-parameters. Some sort of script generates curried instances of all of the multary library functions. Each library function contains a formatted comment specifying the number of parameters to be bound for currying purposes. For example, in `numeric.hpp` there is a function called `clamp`. In the function definition, there is a line
```
// fwd bind count: 2
```
which gets translated by a script into the line
```
fplus_curry_define_fn_2(clamp)
```
which is placed in `curry_instances.autogenerate_defines`, which gets expanded with the macro:
```cpp
#define fplus_curry_define_fn_2(fplus_curry_define_fn_2_name) \
template <typename P1> \
auto fplus_curry_define_fn_2_name(P1 p1) \
{ \
    return [p1](const auto& fplus_curry_p2) \
    { \
        return [p1, fplus_curry_p2](auto&& fplus_curry_p3) \
        { \
            return fplus::fplus_curry_define_fn_2_name(p1, fplus_curry_p2, \
              std::forward<decltype(fplus_curry_p3)>(fplus_curry_p3)); \
        }; \
    }; \
}
```
which is defined in `curry.hpp`.

I don't consider this a viable implementation of curry semantics for exposure to users, and it clearly wasn't design to be.

In my library, I want to avoid macros, and I don't want the user to have to specify the number of arguments they will need, unless currying a variadic function.

## [IO Monad Example](https://gist.github.com/splinterofchaos/3994038)

This code doesn't compile, but I was fascinated by it on cursory reading. I suspect I will draw inspiration from it, if not valid code. (However, I suspect most of the code is quite valid, but I have to figure out why it isn't compiling before I can be sure.)


I Suspect the IO monad here will be the same as in splinterofchaos/Pure.

Features on review:
  * Function composition, functor and monad implementations.

## [splinterofchaos/Pure](https://github.com/splinterofchaos/Pure)—An almost-pure C++ library for writing functional code.

## [splinterofchaos/fu](https://github.com/splinterofchaos/fu)—Functional Utilities for C++

## [fons/functional-cpp](https://github.com/fons/functional-cpp)—functional programming in cpp.

## [GJDuck/libf](https://github.com/GJDuck/libf)—C++ as a Pure Functional Programming Language

## [pfultz2/Fit](https://github.com/pfultz2/Fit)—C++ function utility library http://fit.readthedocs.org

## [awgn/Cat](https://github.com/awgn/cat)—C++14 functional library http://cat.github.io

## [BartoszMilewski/Okasaki](https://github.com/BartoszMilewski/Okasaki)—Functional data structures in C++

## [jhetherly/FCplusplus](https://github.com/jhetherly/FCplusplus)—FC++ library. Functional programming in C++

## [jtomschroeder/lambda](https://github.com/jtomschroeder/lambda)—λ → functional cpp library

## [davber/prelude_cpp](https://github.com/davber/prelude_cpp)—A functional programming library for C++, built on Boost and inspired by Haskell and FC++

## [jdduke/fpcpp](https://github.com/jdduke/fpcpp)—Functional programming with C++11, inspired by Haskell.

## [2012-04-functional-cpp](https://github.com/bfpg/2012-04-functional-cpp)—Immutable data, algebraic types and functional programming in C++
