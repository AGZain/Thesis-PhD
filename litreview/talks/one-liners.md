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
