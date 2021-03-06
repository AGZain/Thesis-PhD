# Introduction

"Software engineering, maybe more than any other engineering discipline, exhibits a rich multiplicity: You can do the same thing in many correct ways, and there are infinite nuances between right and wrong. Each path opens up a new world. Once you choose a solution, a host of possible variants appears, and on and on at all levels—from the system architecture level down to the smallest coding detail. The design of a software system is a choice of solutions out of a combinatorial solution space." ~Andrei Alexandrescu. Modern C++ Design.

<!-- Borrow from Elliot and Hudak 1997 -->

The construction of reliable, efficient control systems software is a difficult task. I believe that much of the difficulty stems from the lack of sufficiently high-level abstractions available in the typically low-level languages of control implementation. In modern C++, higher level abstractions can be built, but there are no standards and very little literature exists to guide the developer in this task. With the progression of modern techniques, and the fusion of control systems with artificial inelegance, the complexity of modern control systems increases boundlessly. Meanwhile, viable hardware architectures becomes more parallel, requiring distributed software architecture to compute control signals. Parallel computing architectures are notoriously difficult to get right, and bugs can be subtle and present stochastically in insignificant numbers of tests.

Many parts of the task can be deferred to tools which automatically generate code. However, those tools can not be expected to work for sufficiently novel control techniques.
