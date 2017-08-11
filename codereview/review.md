# Code review

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->
<!-- code_chunk_output -->

* [Code review](#code-review)
	* [awgn/Cat: C++14 functional library](#awgncathttpsgithubcomawgncat-c14-functional-library)
	* [beark/ftl: C++ template library for fans of functional programming](#bearkftlhttpsgithubcombearkftl-c-template-library-for-fans-of-functional-programming)
			* [Currying](#currying)
	* [Corristo/functionalCpp:](#corristofunctionalcpphttpsgithubcomcorristofunctionalcpp)
	* [Dobiasd/FunctionalPlus: helps you write concise and readable C++ code.](#dobiasdfunctionalplushttpsgithubcomdobiasdfunctionalplus-helps-you-write-concise-and-readable-c-code)
			* [Function composition](#function-composition)
			* [Currying](#currying-1)
	* [eschnett/FunHPC.cxx: FunHPC: Functional HPC Programming](#eschnettfunhpccxxhttpsgithubcomeschnettfunhpccxx-funhpc-functional-hpc-programming)
	* [splinterofchaos/Pure: An almost-pure C++ library for writing functional code.](#splinterofchaospurehttpsgithubcomsplinterofchaospure-an-almost-pure-c-library-for-writing-functional-code)
	* [splinterofchaos/fu: Functional Utilities for C++](#splinterofchaosfuhttpsgithubcomsplinterofchaosfu-functional-utilities-for-c)
	* [fons/functional-cpp: functional programming in cpp.](#fonsfunctional-cpphttpsgithubcomfonsfunctional-cpp-functional-programming-in-cpp)
			* [Notes:](#notes)
			* [List-functor](#list-functor)
	* [jhetherly/FCplusplus: FC++ library. Functional programming in C++](#jhetherlyfcplusplushttpsgithubcomjhetherlyfcplusplus-fc-library-functional-programming-in-c)
	* [GJDuck/libf: C++ as a Pure Functional Programming Language](#gjducklibfhttpsgithubcomgjducklibf-c-as-a-pure-functional-programming-language)
	* [promgamer/functionalcpp: Code examples of functional programming using C++14](#promgamerfunctionalcpphttpsgithubcompromgamerfunctionalcpp-code-examples-of-functional-programming-using-c14)
	* [christianparpart/compose: Functional Programming in C++14](#christianparpartcomposehttpsgithubcomchristianparpartcompose-functional-programming-in-c14)
	* [2012-04-functional-cpp: Immutable data, algebraic types and functional programming in C++](#2012-04-functional-cpphttpsgithubcombfpg2012-04-functional-cpp-immutable-data-algebraic-types-and-functional-programming-in-c)
	* [JIghtuse/functional-cpp: Some examples of Functional C++](#jightusefunctional-cpphttpsgithubcomjightusefunctional-cpp-some-examples-of-functional-c)
	* [ericniebler/fpxx: sandbox for my c++ functional programming experiments](#ericnieblerfpxxhttpsgithubcomericnieblerfpxx-sandbox-for-my-c-functional-programming-experiments)
	* [pfultz2/Fit: C++ function utility library http://fit.readthedocs.org](#pfultz2fithttpsgithubcompfultz2fit-c-function-utility-library-httpfitreadthedocsorg)
	* [oagudo/either-cpp-monad: C++ implementation of the either monad](#oagudoeither-cpp-monadhttpsgithubcomoagudoeither-cpp-monad-c-implementation-of-the-either-monad)
	* [BartoszMilewski/Okasaki: Functional data structures in C++](#bartoszmilewskiokasakihttpsgithubcombartoszmilewskiokasaki-functional-data-structures-in-c)
	* [LoopPerfect/neither: Either and Maybe monads for better error-handling in C++](#loopperfectneitherhttpsgithubcomloopperfectneither-either-and-maybe-monads-for-better-error-handling-in-c)
	* [alexander-bzikadze/Project-Seized-Husky: Standard Haskell library translated to C++ templates.](#alexander-bzikadzeproject-seized-huskyhttpsgithubcomalexander-bzikadzeproject-seized-husky-standard-haskell-library-translated-to-c-templates)
	* [splinterofchaos/io-monad-function.cpp (Gist)](#splinterofchaosio-monad-functioncpphttpsgistgithubcomsplinterofchaos3994038-gist)
	* [ericniebler/meta: A tiny metaprogramming library](#ericnieblermetahttpsgithubcomericnieblermeta-a-tiny-metaprogramming-library)
	* [~~davber/prelude_cpp~~: ~~A functional programming library for C++, built on Boost and inspired by Haskell and FC++~~](#~~davberprelude_cpp~~httpsgithubcomdavberprelude_cpp-~~a-functional-programming-library-for-c-built-on-boost-and-inspired-by-haskell-and-fc~~)

<!-- /code_chunk_output -->



## [awgn/Cat](https://github.com/awgn/cat): C++14 functional library

Features on review:
  * Currying
  * Concepts
  * Category theoretical traits and interfaces


## [beark/ftl](https://github.com/beark/ftl): C++ template library for fans of functional programming

Features on review:
  * Currying
  * Concepts
  * Category theoretical traits and interfaces


#### Currying

A general currying mechanism is provided in `prelude.h`. However, that header
only provides an interface. The support for curried functions comes from a
`std::function`-like type-erasure wrapper specified in `function.h`. The
documentation therein claims that the main difference between an `stl::function`
and `std::function` is the support for curried calling.

The STL library has an interesting trait: `is_monomorphic`, which


## [Corristo/functionalCpp](https://github.com/Corristo/functionalCpp):
C++14 with typeclasses, monads, ...

Notes:
  * Cited in [this](https://stackoverflow.com/a/39730419/1827360) Stack Overflow answer posted to a question titled _Monad interface in C++_

  * For a more minimal version of the monadic interface, [see here](http://coliru.stacked-crooked.com/a/4c63d1251a74c82c).

  Features on review:
    * Currying
    * Concepts
    * Category theoretical traits and interfaces

## [Dobiasd/FunctionalPlus](https://github.com/Dobiasd/FunctionalPlus): helps you write concise and readable C++ code.

This library is associated with a [udemy course](https://www.udemy.com/functional-programming-using-cpp/) that has two [YouTube videos](https://www.youtube.com/watch?v=jD8Tu1tqvZo) available for preview. I haven't taken the course, but this library is publicly available.

Features on review:
  * Function composition
  * Currying
  * Function traits
  * Intermediate value elision in the `fwd` namespace. (Is it lazy?)
  * [Gradient decent algorithm](
    https://github.com/Dobiasd/FunctionalPlus/blob/master/include/fplus/optimize.hpp)

#### Function composition



#### Currying
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



## [eschnett/FunHPC.cxx](https://github.com/eschnett/FunHPC.cxx): FunHPC: Functional HPC Programming

This is FunHPC.cxx, a C++ library that provides fine-grained multi-threading for distributed-memory systems in a functional programming style.

* Check out `CONTRIBUTING.ris`.

Features on review:
* List-monad:
- FunHPC.cxx/fun/vector.hpp
- FunHPC.cxx/fun/array.hpp

* Maybe-monad: FunHPC.cxx/fun/maybe.hpp

* Either-monad: FunHPC.cxx/fun/either.hpp

* Empty-monad: FunHPC.cxx/fun/empty.hpp

* Function-monad: FunHPC.cxx/fun/function.hpp

* Traits



## [splinterofchaos/Pure](https://github.com/splinterofchaos/Pure): An almost-pure C++ library for writing functional code.

Features on review:
  * Currying
  * Concepts
  * Category theoretical traits and interfaces



## [splinterofchaos/fu](https://github.com/splinterofchaos/fu): Functional Utilities for C++

Features on review:



## [fons/functional-cpp](https://github.com/fons/functional-cpp): functional programming in cpp.

#### Notes:
  * Very strange that list-monad/functor are implemented for `std::list` and `std::forward_list`, but not vector!
  * Uses `std::function` and `std::bind` in functor and monad implementations
  * `map` defined in `map.hpp` for `std::forward_list` uses insert_front.

Features on review:
  * list-monad
  * list-functor

#### List-functor

In `functional-cpp/src/map.hpp` functor-maps for `std::list` and `std::forward_list` are defined. The functor itself is fleshed out in `functional-cpp/src/functor.hpp`, where `fmap` simply forward to `map` from `map.hpp`.

For some reason that I can't figure out, there are `map` overloads for both `std::forward_list` and `std::list` on whether or not the type `B` in `f : A → B` is deduced or specified as a template argument. If `B` is specified, a hand-rolled loop is used to apply the function to the elements, but if it is deduced `std::transform` is used. Strangely enough, the case where `B` is specified for the `std::forward_list` uses `std::function` in the signature instead of templatising on the callable type.

In the map functions, lists are passed by reference and callables are copied. It doesn't look like a lot of thought went into value/reference semantics.



## [jhetherly/FCplusplus](https://github.com/jhetherly/FCplusplus): FC++ library. Functional programming in C++

Notes:
  * No functor or monad based on standard containers. There is a lazy list implementation.

Features on review:
  * Category theoretical traits and interfaces
  * Lazy list

  ## [jdduke/fpcpp](https://github.com/jdduke/fpcpp): Functional programming with C++11, inspired by Haskell.

Notes:
  * List functor is built around the library's own lazy list.

  fpcpp (functional programming in C++) is a lightweight, header-based C++ library for enabling functional programming style and features in modern C++ programs.

  Features on review:
    * Lazy list



  ## [jtomschroeder/lambda](https://github.com/jtomschroeder/lambda): λ → functional cpp library

Advertised Features:
  * currying
  * function composition
  * partial application (simplified functional bind)
  * streams

Notes:
  * The closest thing to a list-functor revolves around the stream structure.

Features on review:
  * Streams



## [GJDuck/libf](https://github.com/GJDuck/libf): C++ as a Pure Functional Programming Language

Notes:
  * There's some sort of list-monad, but it doesn't relate to standard containers and isn't very readable.

Features on review:
  * ?



## [promgamer/functionalcpp](https://github.com/promgamer/functionalcpp): Code examples of functional programming using C++14

Notes: Just some code from a talk. Not much useful here.

Features on review:
  * ?



## [christianparpart/compose](https://github.com/christianparpart/compose): Functional Programming in C++14

This presents a really nice API for composing functions:
```cpp
#include "compose.h"
#include <iostream>

int main() {
  auto v = {1, 2, 3, 4, 5, 6, 7, 8};

  auto range = compose(v)
                   .map([](auto x) { return x * x; })
                   .select([](auto x) { return !(x % 2); })
                   .take(3);

  for (auto a: range) {
    std::cout << "a: " << a << std::endl;
  }
}
```

Features on review:
  Composition API



## [2012-04-functional-cpp](https://github.com/bfpg/2012-04-functional-cpp): Immutable data, algebraic types and functional programming in C++

Notes:
* No fmap of any kind.
* Seems focused on an optional type.

Features on review:



## [JIghtuse/functional-cpp](https://github.com/JIghtuse/functional-cpp): Some examples of Functional C++

Notes:
  * No monads.

Features on review:
  * Composition and currying.



## [ericniebler/fpxx](https://github.com/ericniebler/fpxx): sandbox for my c++ functional programming experiments

Notes:
  * No list-monad.

Features on review:
  * State-monad: fpxx/include/fpxx/monad/state.hpp
  * Category theoretical traits and interfaces
  * Currying



## [pfultz2/Fit](https://github.com/pfultz2/Fit): C++ function utility library http://fit.readthedocs.org

Features on review:
* Capture function decorator in `capture.hpp`, provides more flexibility than lambda capture, including move and perfect capturing.

* Composition (see `include/fit/compose.h`)

* Piping (see `include/fit/pipable.h`)



## [oagudo/either-cpp-monad](https://github.com/oagudo/either-cpp-monad): C++ implementation of the either monad

Features on review:



## [BartoszMilewski/Okasaki](https://github.com/BartoszMilewski/Okasaki): Functional data structures in C++

Features on review:



## [LoopPerfect/neither](https://github.com/LoopPerfect/neither): Either and Maybe monads for better error-handling in C++

Features on review:



## [alexander-bzikadze/Project-Seized-Husky](https://github.com/alexander-bzikadze/Project-Seized-Husky): Standard Haskell library translated to C++ templates.

Seems like a partial implementation of Haskell's list type.

Features on review:



## [splinterofchaos/io-monad-function.cpp](https://gist.github.com/splinterofchaos/3994038) (Gist)

This code doesn't compile, but I was fascinated by it on cursory reading. I suspect I will draw inspiration from it, if not valid code. (However, I suspect most of the code is quite valid, but I have to figure out why it isn't compiling before I can be sure.)


I Suspect the IO monad here will be the same as in splinterofchaos/Pure.

Features on review:
  * Function composition, functor and monad implementations.



## [ericniebler/meta](https://github.com/ericniebler/meta): A tiny metaprogramming library

Features on review:
* Metaprogramming techniques and tools.

See:
* http://ericniebler.com/2014/11/13/tiny-metaprogramming-library/
* https://ericniebler.github.io/meta/index.html



## [~~davber/prelude_cpp~~](https://github.com/davber/prelude_cpp): ~~A functional programming library for C++, built on Boost and inspired by Haskell and FC++~~

It seems there was never a first commit.
