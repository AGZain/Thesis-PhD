# Bartosz Milewski - Category Theory for Programmers I

Playlist: [click here](https://www.youtube.com/playlist?list=PLbgaMIhjbmEnaH_LTkxLI7FMa2HsnawM_)

***Category theory for programmers by Bartosz Milewski. Seattle, Summer 2016. Additional material [here](https://bartoszmilewski.com/2014/10/28/category-theory-for-programmers-the-preface/).***



## [1.1 Motivation and Philosophy](https://youtu.be/I8LbkfSSR58?list=PLbgaMIhjbmEnaH_LTkxLI7FMa2HsnawM_)


* Mostly familiar background



## [1.2 What is a category?](https://youtu.be/p54Hd7AmVFU?list=PLbgaMIhjbmEnaH_LTkxLI7FMa2HsnawM_)


* Mostly familiar background



## [2.1 Functions, epimorphisms](https://youtu.be/O2lZkr-aAqk)


* A good example of a function which can't be pure: `getchar()`. Think about memoising it.

* A [cute example](https://youtu.be/O2lZkr-aAqk?t=21m28s) of an isomorphism  between natural numbers and even numbers.
  - No [such isomorphism](https://youtu.be/O2lZkr-aAqk?t=22m28s) between natural numbers and real ones.

  Illustration of a fiber:
    ![](fiberation-1.jpg)

  FYI: Fiber product as defined in Spivak [p. 54]. Given the following relationships
  ```@mermaid
    graph TB;
    X--"f"--> Z;
    Y--"g"--> Z;
  ```
  the _fiber product_ is the set $
    X\times_Z Y := \{(x,z,y)\ |\ f(x) = z = g(y)\}.
  $
  Consolodating those ideas is interesting.

* > So if my microscope doesn't work, maybe my telescope will work.

  A [Cute idea](https://youtu.be/O2lZkr-aAqk?t=36m) and comment in reference to the idea that cetegory theory doesn't allow you to define relationships by the internal structore of the objects. So, things such as isomorphism must be defined looking outward, not inward, since we treat objects as points with no internal structure.

* A beautiful [discussion](https://youtu.be/O2lZkr-aAqk?t=36m49s) of how category theorists prefer greek roots, and have epic ↔ surjection and monic ↔ injection. Thus, epimorphisms and monomorphisms.

* The Wikipedia definition of [epimorphism](https://en.wikipedia.org/wiki/Epimorphism) is somewhat abstruse. I find Bartosz's [explanation](https://youtu.be/O2lZkr-aAqk?t=39m9s) illuminating.



## [2.2 Monomorphisms, simple types](https://youtu.be/NcT7CGPICzo)


* Bartosz gives a good [explaination](https://youtu.be/NcT7CGPICzo?t=1m42s)  of monomorphism, a la his explanation of epimorphism from the end of the last lecture.


## [3.1 Examples of categories, orders, monoids](https://youtu.be/aZjhqkD6k6w)


* How to build a category from any graph: [_free construction_](https://youtu.be/aZjhqkD6k6w?t=9m52s)

* NB: According to [Wikipedia](https://en.wikipedia.org/wiki/Posetal_category),
  > In mathematics, a posetal category, or thin category, is a category whose homsets each contain at most one morphism.

* NB: Preorders may be cyclic and not all objects may be connected, but all hom-sets contain at most one arrow. Partial orders are acyclic but still, not all elements may be comparable, and total orders are acyclic where exactly one arrow exists between all objects.

* Very nice [explanation](https://youtu.be/aZjhqkD6k6w?t=25m11s) of why epic monomorphisms (or monic epimorphisms?) aren't generally isomorphisms, despite the fact that bijections on sets are isomorphisms.

* [Monoid](https://youtu.be/aZjhqkD6k6w?t=32m47s)



## [3.2 Kleisli category](https://youtu.be/i9CU4CuHADQ)


* C\+\+ audit trail [example](https://youtu.be/i9CU4CuHADQ?t=9m14s).



## [4.1 Terminal and initial objects](https://youtu.be/zer1aFgj4aU)


* Video begins with a review of Kleisli category, which I find very effective. I prefer it to the one in the last video, though I think it is valuable to have them both.

* Final diagram in Kleisli discussion is a nice illustration of a monad.
  ![](kleisli-caegory.jpg)



## [4.2 Products](https://youtu.be/Bsdl_NKbNnU)


* `std::pair.first` is the projection function for the direct product.



## [5.1 Coproducts, sum types](https://youtu.be/LkIRsNj9T-8)


* A coproduct on sets gives a 'tagged union', also called a _variant_ which explains the C\+\+ naming `std::variant`. https://youtu.be/LkIRsNj9T-8?t=17m13s



## [5.2 Algebraic data types](https://youtu.be/w1WMykh7AxA)


* Relatively shocking [type-algebra example](https://youtu.be/w1WMykh7AxA?t=24m19s) of power series giving all possible lists:
  ![](type-algebra-problem.jpg)



## [6.1 Functors](https://youtu.be/FyoQjkwsy7o)


* A set is a category with only identity arrows. The elements of the set are objects of the category. It is called a discrete category.

* A category that is not discrete, has structure.

* Classes of functors:
  - Faithful functor: injective on hom-sets.
  - Full functor: surjective on hom-sets.
  - Fully faithful functor is bijective on hom-sets.
  - Constant functor, $\mathit{\Delta_C}$, maps all objects into a single fixed one, and all arrows into the indentity arrow of the fixed object.



## [6.2 Functors in programming](https://youtu.be/EO86S2EZssc)


*



## [7.1 Functoriality, bifunctors]()

## [7.2 Monoidal Categories, Functoriality of ADTs, Profunctors]()

## [8.1 Function objects, exponentials]()

## [8.2 Type algebra, Curry-Howard-Lambek isomorphism]()

## [9.1 Natural transformations]()

## [9.2 Bicategories]()

## [10.1 Monads]()

## [10.2 Monoid in the category of endofunctors]()
