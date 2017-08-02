# Functional Programming

Functional programming is a paradigm. It is a constellation of ideas forming a framework for looking at problems in computer programming.

This framework transends the features of the language of implementation. However, the features available will affect the fidelity to which those ideas can be transcribed.

Differentiate a function value from it's definition. Here are two equivalent definitions of the same function:
```cpp
int twofold(int x) { return x + x; }
```
vs.
```cpp
int twofold(int x) { return 2 * x; }
```
It can be asserted mathematically that these are equivalent. But regarded as procedures for computation, one may be more or less _performant_ with a given compiler, on a given set of hardware. The notion of performance is not one that can be attributed to the function value, but only to the particular definition in the context of the machinery that evaluates it.
