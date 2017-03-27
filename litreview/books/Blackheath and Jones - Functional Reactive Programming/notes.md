# Blackheath & Jones - Functional Reactive Programming

Spiratic notes.

These notes are not intended to be comprehensive. It's just a scratch pad for things I want to remember later.

* The book mentions, in Ch. 1 or 2, that formulations of FRP that contain the 'signal' primitive are often ones that don't distinguish between behaviours and events (i.e., Cells and Streams, respectively, in ther vernacular of the book.) This comment is relate to the RT-FRP system of Hudak and others which introduces a morphism `Event`$\alpha \simeq$`Behaviour(Maybe`$\alpha$`)`, and the unified concept is called a signal. For details, see original works, or Evan Czaplicki's PhD thesis, p. 11.
