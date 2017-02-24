# Steven Roman - Introduction to Category Theory Lectures

Playlist: [click here](https://www.youtube.com/playlist?list=PLiyVurqwtq0Y40IZhB6T1wM2fMduEVe56)

***A series of lectures presented by the mathematician [Steven Roman](www.sroman.com)***


## [Lecture 1](https://youtu.be/If6VUXZIB-4)

Five basic concepts in category theory:
* categories
* functors
* natural transformations
* universality
* adjoints

Classes are more general sets. All sets are classes, but not all sets are classes. A class cannot be a member of a class. So, there is no set of all sets (because of some well known paradoxes), but there is a class of all sets.

From Wikipedia entry for [Class](https://en.wikipedia.org/wiki/Class_(set_theory)):
> The paradoxes of naive set theory can be explained in terms of the inconsistent assumption that "all classes are sets". With a rigorous foundation, these paradoxes instead suggest proofs that certain classes are proper (i.e., that they are not sets). For example, Russell's paradox suggests a proof that the class of all sets which do not contain themselves is proper, and the Burali-Forti paradox suggests that the class of all ordinal numbers is proper. The paradoxes do not arise with classes because there is no notion of classes containing classes. Otherwise, one could, for example, define a class of all classes that do not contain themselves, which would lead to a Russell paradoxes for classes.

***Definition:*** A ***category***, $\mathcal{C}$, consists of the following:
 1. A class $\text{Obj}(\mathcal{C})$ of objects. Notation: instead of writing $A\in \text{Obj}(\mathcal{C})$, we right $A\in\mathcal{C}$.

 2. For each pair of objects $A, B\in\mathcal{C}$ there exists a *set* called the *hom* set for $(A, B)$, $\hom_\mathcal{C}(A,B)$. The elements of a homeset are called *morphisms*, *maps* or *arrows*.
    * NB: $\hom(A,B) \neq \hom(B,A)$.
    * We use function notation, but morphisms need not be functions. For example, $f\in\hom(A,B)$ is a morphism $f:A\rightarrow B$, with domain $A$ and codomain $B$.
    * A non-standard notation that is used in this series: a shorthand for $f:A\rightarrow B$ is $f_{AB}$.

 3. Not a universal condition, but by convention: distinct hom sets are disjoint.

 4. Composition of morphisms: if $f:A\rightarrow B$ and $g:B\rightarrow C$ then $g\circ f: A\rightarrow C$ s.t. $f\circ(g\circ h) = (f\circ g) \circ h$ (that is, composition is associative). Composition on works with alignment of domains and codomains. In a composition of a pair, the codomain of one must be the domain of the other.

 5. Identity morphisms: for each $A\in\mathcal{C}$ there exists $1_A: A \rightarrow A$ for which $1_B \circ f_{AB} = f_{AB} \circ 1_B = f_{AB}$
    * Notation: the class of morphisms in $\mathcal{C}$: $\text{Mor}(\mathcal{C})$. If hom-classes are used instead of hom sets, then when the hom classes are in fact hom sets for a particular category, that category is said to be ***locally small***. Sets are thought of as smaller than classes in general. The lecturer specifies that all hom classes have to be hom sets, so all "of our" categories are locally small.
    * Notation: if $\text{Obj}(\mathcal{C})$ and $\text{Mor}(\mathcal{C})$ are sets, then $\mathcal{C}$ is said to be a ***small category***.

### [Examples](https://youtu.be/If6VUXZIB-4?t=25m8s)

* Sets. $\text{Obj}(\text{sets}) = \text{all sets}$.  $\text{Mor}(\text{sets}) = \text{set functions}$. (Usually never intrested in the class of all morphisms in a category. Focus locally on hom-sets between two specific objects.) $\hom(A,B) = \{\text{set functions from\ } A \text{\ to\ } B\}$.

* Grps (Groups). Objects is the class of all groups, and the hom-set $\hom(G,H)$ are the group homomorphisms from $G$ to $H$.

* AbGrps (abelian groups). Same as groups, but the objects are only abelian.

* $\text{Mods}_R$ (Modules over a ring). Objects are R-modules and morphisms are R-maps.

* $\text{Vect}_F$ (vector spaces over a field.) The morphisms are the linear transformations.

* …

* Fields - morphisms are ring embeddings

* Posets - objects are the class of all partially ordered sets and the morphists are monotone maps: $a \leq b \ \Longrightarrow\ fa\leq fb$ (maps preserving inequality structure).

* …

### [More unusual Examples](https://youtu.be/If6VUXZIB-4?t=30m24s)

* Matricies over a field

* Monoids - a category with no objects, and the morphisms are the elements of the set, which are built up by composition. So the morphism $1: \bullet\rightarrow\bullet$ can be composed with itself to make $2:\bullet\rightarrow\bullet$.

   I found a nice bit about this on [this stack exchange post](http://math.stackexchange.com/a/1332726/49718):
>You already know that a monoid $M$ is a set with a unit $e$ and a binary operation. More precisely, if $a,b,c\in M$ then $$a\circ b\in M$$ $$(a\circ b)\circ c=a\circ (b\circ c)$$ $$e\circ a=a\circ e=a$$
>
>Now, take any category $C$ with one object, $c$. Since $C$ is a category, we need to say what the arrows are. That is, what the morphisms $c\rightarrow c$ are. There must be a unit $1_{c}:c\rightarrow c$, the arrows must be composeable and the composition must be associative. More precisely, if $f,g$ and $h$ are arrows, then $$f\circ g\in \text{Morph}(C)$$ $$(f\circ g)\circ h= f\circ (g\circ h)$$ $$1_{c}\circ f=f\circ 1_{c}=f$$Notice we are $\textit not$ talking about sets here. Just objects and arrows, in the abstract.
>
>But now if we just observe that the operations on $M$ are $\textit exactly$ the same as the operations on $\text{Morph}(C)$, we may regard the category $C$ as the monoid $M$. This correspondence is reversible: given category $C=\left \{ c \right \}$ we obtain a monoid $M$ whose elements are the arrows of $C$.
>
> Thus the two descriptions are equivalent.
>
> All this works because the binary operations are the same for both structures.


* …

* [Deductive System of Logic](https://youtu.be/If6VUXZIB-4?t=38m3s)

### [—————————](https://youtu.be/If6VUXZIB-4?t=40m57s)

 1. Morphisms are just as important as the things they morph.
 2. Some mathematical notions are best described in terms of morphisms, not elements.

[Finally](https://youtu.be/If6VUXZIB-4?t=43m42s), a neat explanation of projection maps and how any ordered triple $(U, \rho_1, \rho_2)$ where $U$ is the direct product $V\times W$, and $\rho_1(v, w) = v$ and $\rho_2(v,w) = w$ is isomorphically equivalent to any other such triple.

This is demonstrated on the direct product of vector spaces $V\times W$:
$$
  V\times W = \{(v,w) | v\in V, w\in W\}
$$

The functions $\rho_1$ and $\rho_2$ are product maps:
$$
  \rho_1 : V\times W \rightarrow V;\qquad \rho_1(v,w) = v
$$

$$
  \rho_2 : V\times W \rightarrow W;\qquad \rho_2(v,w) = w
$$

It's possible to show that this ordered tripple, $(V\times W, \rho_1, \rho_2)$, has a special property called the universal property. It is illustrated (and stated) in the folowing diagram:
![](universal-property-1.svg)

This characterises the direct product in the following sense. If $(U,\lambda_1, \lambda_2)$ with $\lambda_1: U\rightarrow V$ and $\lambda_2: U\rightarrow W$ has this universal property, then $U \simeq V\times W$.

So, if you're willing to accept that any two vector spaces that are isomorphic are "almost the same", then the universal property describes the direct product.

In more advanced courses in mathematics, mapping properties like this are used as the definition. The example of the gree group is given, which may be defined in terms of a universal mapping property.


## [Lecture 2](https://youtu.be/leFJdbZy7Ys)

### Functors

Morphisms between cetigories. If we have catigories $\mathcal{C}$ and $\mathcal{D}$, and wish to define a morphism from one to the next, then we'll need two functions: one to define the mapping of objects and the other to define the mapping of arrows between the two catagories. We define
$$
  F:\mathcal{C}\Rightarrow\mathcal{D}
$$
where $F$ represents both of those functions:
$$
  F: \text{Obj}(\mathcal{C}) \rightarrow\text{Obj}(\mathcal{D})
$$

$$
  F: \text{Mor}(\mathcal{C}) \rightarrow\text{Mor}(\mathcal{D})
$$
There are covariant and contravariant flavours of the arrow morphism:
  * Covariant:
    $$
      F: \text{Hom}_\mathcal{C}(A,B) \rightarrow \text{Hom}_\mathcal{D}(FA, FB)
    $$
  * Contravariant:
    $$
      F: \text{Hom}_\mathcal{C}(A,B) \rightarrow \text{Hom}_\mathcal{D}(FB, FA)
    $$
    Notice the domain and codomain are swapped in $\mathcal{D}$.

These morphisms must preserve the structure of the category. So,
* Identity: $F1_A = 1_{FA}$
* Composition:
  * Covariant: $F(g\circ f) = Fg\circ Ff$
  * Contravariant: $F(g\circ f) = Ff\circ Fg$. So, composition is preserved, but reversed in the contravariant case, since the domains and codomains of the arrows are swapped in a covariant functor.

Notationally, $F$ restricted to a given hom-set, $F|_{\text{Hom}_\mathcal{C}(A,B)}$, is called the *local arrow part* of the functor.

A helpful way to view a functor is as a map from one arrow diagram

$$
  A\rightarrow_f B \Rightarrow_F FA\rightarrow FB
$$

(Swap $FA$ and $FB$ for contravariant case.)

Graphically, this may be illustrated like so:
![](functor-illustration.svg)
