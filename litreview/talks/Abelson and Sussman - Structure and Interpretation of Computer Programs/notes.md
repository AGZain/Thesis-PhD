# Bartosz Milewski - Category Theory for Programmers I

Playlist: [click here](https://www.youtube.com/playlist?list=PLE18841CABEA24090)

***This course introduces students to the principles of computation. Upon completion of 6.001, students should be able to explain and apply the basic methods from programming languages to analyze computational systems, and to generate computational solutions to abstract problems. Substantial weekly programming assignments are an integral part of the course. This course is worth 4 Engineering Design Points.***

***This course features projects and supporting documentation. This course has virtually all of its course materials online. 6.001 is the first course in the core of departmental subjects which is required for all undergraduates in Electrical Engineering and Computer Science. It offers an online version of the textbook for the course, Structure and Interpretation of Computer Programs, 2nd ed., by Abelson, Sussman, and Sussman.***

[Readings](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-001-structure-and-interpretation-of-computer-programs-spring-2005/readings/) including textbook pdf.


## [Overview and Introduction to Lisp](https://youtu.be/2Op3QLzMgSY?list=PLE18841CABEA24090)

 * 00:30 Computer science is a terrible name. First, it's not a science. And it's also not about computers.
 * 3:12 People in the future will recognize that people were really formalizing intuitions about process -- how to do things. Talking precisely about how to knowledge. As opposed to geometry that talks about what is true.
 * 5:36 What's a process? A process is like a magical spirit that lives in the computer and does something. What directs a process is a pattern of rules called a procedure. Procedures are the spells. The programming language is the language for casting the spells.
 * 7:25 Computer science is the business is in formalizing the "how to" imperative knowledge.
 * 10:12 As opposed to the constraints in other kinds of engineering,  where the constraints of what you can build are the constraints of physical systems, the constraints imposed in building large software systems are the limitations of our own minds.
 * 10:55 Abstraction. Engineering technique whereby a "black box" can be used without knowing its implementation details. And these "black boxes" can be combined to create even more complex systems.
 * 16:50 We're not only building boxes that input and output numbers. We're building boxes that can compute methods. We can have procedures whose values is another procedure.
 * 18:14 Big Topic 1: Black-Box Abstraction
 * 22:45 Big Topic 2: Conventional Interfaces
 * 24:45 Big Topic 3: Metalinguistic Abstraction - making new languages

 * 28:07 Learning a new language. Know: 1) primitive elements 2) means of combination and 3) means of abstraction.
 * 29:58 Lisp's primitive data
 * 38:45 Lisp's "define"
 * 44:48 Lambda is Lisp's way of saying "make a procedure".
 * 49:33 A key thing in Lisp is that you don't make arbitrary distinctions between things that happen to be primitive in the language and things that happen to be built in. So the things you construct get used with all the power and flexibility as if they were primitives.
 * 51:13 How to make a case analysis i.e.conditionals. "cond" or "if"
 * 59:05 An example problem: Heron's square root algorithm
 * 1:08:54 Summary﻿

## [Overview and Introduction to Lisp](https://youtu.be/2Op3QLzMgSY?list=PLE18841CABEA24090)




While O-O programming focuses on encapsulation of data, functional programming allows us to encapsulate behaviour.

As an example take this algorithm for adding up the integers from $a$ to $b$:
```
(define (sum-integers a b)
  (if (> a b)
      0
      (+ a (sum-integers (+ a 1) b))))
```
or in C++
```
int sum_int(int a, int b) {
  if (a > b)
    return 0;
  else
    return a + sum-int(++a, b);
}
```
This will compute $\sum_{i=a}^b i$. Likewise, the following code will sum the squares of the integers from $a$ to $b$ as $\sum_{i=a}^b i^2$:
```
(define (sum_sqrs a b)
  (if (> a b)
      0
      (+ (* a a) (sum-sqrs (+ a 1) b))))
```
```
int sum_sqrs(int a, int b) {
  if (a > b)
    return 0;
  else
    return a*a + sum-sqrs(++a, b);
}
```
A yet more complex example produces a sum which converges (slowly) to $\pi/4$ using Leibniz's formula
$$
  \frac{\pi}{4} = \sum_{i=0}^{\infty} \frac{2}{(4\,n+1)\,(4\,n+3)}
$$
```
(define (<name> a b)
(if (> a b)
    0
    (+ (<term> a)
       (<name> a b))))
```

$\sum_{i = a}^{b} f(x)$

```
int <name>(int a, int b)
  if (a > b)
    return 0;
  else
    return f(a) + <name>(++a, b)
```

```
int accumulate_range(std::function<int(int)> f, int a, int b) {
  if (a > b)
    return 0;
  else
    return f(a) + accumulate_range(++a, b)
}

int sum_int (int a, int b) {
  return accumulate_range([](int x){return x;} , a, b)
}

int sum_sqr (int a, int b) {
  return accumulate_range([](int x){return x*x;} , a, b)
}

int approx_pi(int b) {
  auto f = [](int x){
    return 2. / (4*x + 1) / (4*x + 3);
  };
  return accumulate_range(f, 0, b)
}
```


```
accumulate(iota(0, 6) | transform(f), 0 );
```
