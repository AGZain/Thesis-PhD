# One-line points and Brief Quotes

* > We believe that FRP isn't so much a cleaver idea as something fundamental: that when motivated people independently try to fix the observer pattern, after much stumbling, they will eventually converge on similar solutions; and and that there are only a few possible variations in that "perfect" design. … FRP is a discovery, not an invention.

    - Stephen Blackheath, Anthony Jones *Functional Reactive Programming* p. 9


* > "Have you tried restarting it?" or *Why State is Problematic*

    - Section 1.10 title, Stephen Blackheath, Anthony Jones *Functional Reactive Programming* p. 9


* > When complex parts interact in complex ways, complexity compounds.

    - Stephen Blackheath, Anthony Jones *Functional Reactive Programming* p. 10


* > In FRP we talk about working in the *problem space*, rather than the machine space.

    - Stephen Blackheath, Anthony Jones *Functional Reactive Programming* p. 10


* > *Competence without comprehension*

    - A turn of phrase borrowed from Daniel Dennett


* NB: In 1998, readers of Software Development magazine named Steve McConnell as one of the three most influential people in the software industry along with Bill Gates and Linus Torvalds. Former editor and cheif of IEEE Software Magazine.


* > Anyone who's studied physics is familiar with the fact that while physics—like history—does not precisely repeat itself, it does rhyme, with similar structures at different scales of length and energy.
    - Edward Witten in his talk "What Every Physicist Should Know About String Theory" at conference Strings 2015, Bengaluru, India.

* Good point: on _modern_ CPUs, one of the most expensive things we can do is a conditional jump. My immediate thought is the comperable overhead of multiplying optional values. There will be an inlined function call, and something tantamount to 2 null pointer checks added to every operation, but if it's paged in the cache, those should be much quicker than a jump, which can't be optimised by the compiler.
    - [Talk by Douglas Crockford](https://youtu.be/99Zacm7SsWQ?t=44m42s) at NDC 2017


* > So if my microscope doesn't work, maybe my telescope will work.

  A [Cute idea](https://youtu.be/O2lZkr-aAqk?t=36m) and comment in reference to the idea that category theory doesn't allow you to define relationships by the internal structure of the objects. So, things such as isomorphism must be defined looking outward, not inward, since we treat objects as points with no internal structure.


* On category theory in programming:
  > we can reason a out these things in the abstract: tease out relationships that relying on assumptions of constraint, giving us proofs of behaviour and safety without working anew with each specific implementation. If I can recognise that something has the properties of a monoid, I can divide an conquor without worrying over the specifics of each case.

    - Me.


* > The type constructor lives in a different namespace than the data constructor: they never get confused by the compiler. They get confused by people, but people can be trained, unlike compilers.

  - Bartosz Milewski https://youtu.be/wtIKd8AhJOc


* > In control systems, thorough unit testing is critical. This creates a conflict with the object-oriented paradigm, since data-hiding impedes testing by preventing calls to non-public class methods. It is often difficult to strike the right balance between transparency and encapsulation. Functional programming avoids this collision, since state minimised within the paradigm, but not encapsulated. There are no private methods, so everything is testable.

  - Me.



* >  The argument for the distinction between behaviors and events is that their API is quite different. The main point is that they have different product types:
  >
  ```
  (Behavior a , Behavior b) = Behavior (a,b)
  (Event a    , Event b   ) = Event (a :+: b)
  ```
  >  In words: a pair of behaviors is the same as a behavior of pairs, but a pair of events is the same as an event from either component/channel. Another point is that there are two operations
  >
  >
  ```
  (<*>) :: Behavior (a -> b) -> Behavior a -> Behavior b
  apply :: Behavior (a -> b) -> Event a    -> Event b
  ```
  > that have almost the same type, but quite different semantics. (The first updates the result when the first argument changes, while the second doesn't.)
  >
  >  To summarize: signals can be used for implementing FRP and are valuable for experimenting with new implementation techniques, but behaviors and events are a better abstraction for people who just want to use FRP.

  - Heinrich Apfelmus http://stackoverflow.com/a/7453062/1827360
