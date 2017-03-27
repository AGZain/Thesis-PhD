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

## [3.1 Examples of categories, orders, monoids]()

## [3.2 Kleisli category]()

## [4.1 Terminal and initial objects]()

## [4.2 Products]()

## [5.1 Coproducts, sum types]()

## [5.2 Algebraic data types]()

## [6.1 Functors]()

## [6.2 Functors in programming]()

## [7.1 Functoriality, bifunctors]()

## [7.2 Monoidal Categories, Functoriality of ADTs, Profunctors]()

## [8.1 Function objects, exponentials]()

## [8.2 Type algebra, Curry-Howard-Lambek isomorphism]()

## [9.1 Natural transformations]()

## [9.2 Bicategories]()

## [10.1 Monads]()

## [10.2 Monoid in the category of endofunctors]()
