---
description: What is a boolean anyway?
icon: binary
---

# 0's and 1's

From your early days of studying math, you may remember some basic boolean algebra. Specifically, you probably already understand the operations Not, And, Or.&#x20;

If we have three numbers  $$a,\ b,\ c$$, then the expression

<p align="center"><span class="math">(a\vee b)\wedge \neg c</span></p>

\
in English would read as $$(a \text{ OR }b)\text{ AND NOT }c$$ . If either $$a$$ or $$b$$ is true (1), then the whole bracket is true. If $$c$$ is false (0), then $$\neg c$$ is true, and vice-versa. The $$\text{AND}$$ operator requires that both the bracket and $$\neg c$$ be true for the whole expression to be true.&#x20;

## Mathematical notation

Since the symbols $$\vee, \wedge, \neg$$ are quite different from our standard mathematical operations, we can simply treat true or false as 1 and 0 and the expression above can be suddenly written as:

<p align="center"><span class="math">(a+b)\cdot\overline{c}</span></p>

\
When we treat boolean algebra as base-2 math (only 0's and 1's), the only new symbol is the negation, which simply inverts a 0 to a 1 and vice-versa. We'll find this assumption works quite intuitively.

* $$a+b$$: If both are zero ($$0+0=0$$) the expression is false. If either is one, ($$0+1=1$$), the expression is true. If both are one, $$1+1=1$$.
* $$a\cdot b$$: Similar to addition, you'll find this expression is true only when $$a=1,\ b=1$$, since multiplying anything by zero makes it all zero.

<details>

<summary>Why does 1 + 1 = 1 ?</summary>

As opposed to elemental algebra, boolean algebra only has two values: 0 and 1. While the symbols $$+,~\cdot~$$ are shared, and many properties of real numbers in elemental algebra apply to boolean algebra, they operate on different sets of numbers with different operations. In elemental algebra, $$1+1=2$$, however in boolean algebra, we get $$1+1=1$$. Logically, the expression "true OR true" is just "true".\
\
To drive the point further home, we can apply boolean algebra to physics, where 0 is a closed switch and 1 is an open switch. In a circuit such as:

<p align="center"><img src="https://cdn.prod.website-files.com/6634a8f8dd9b2a63c9e6be83/669df6a60c126b798dce62d9_308369.image0.jpeg" alt="" data-size="original"><br><sub><em>Source:</em></sub> <a href="https://www.dummies.com/article/technology/electronics/circuitry/electronics-projects-how-to-build-series-and-parallel-switched-circuits-180195/"><sub><em>dummies.com</em></sub></a></p>

The top circuit represents $$a \cdot b$$, both must be 1 (on) to light the bulb.

The bottom circuit represents $$a+b$$, at least one must be 1 (on) to light the bulb. \
If both are on, the result is the same as if only one were one - the resulting signal from this parallel block is **on** - voltage passes through. \
\
In other words, $$1+1=1$$.

</details>

We'll use only this notation from now on.&#x20;

