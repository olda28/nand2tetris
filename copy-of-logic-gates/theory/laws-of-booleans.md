---
description: >-
  Very often, we'll get quite an ugly expression, and we'll want to simplify it.
  Just like in normal mathematical expressions. You know, the ones with normal
  numbers.
icon: scale-balanced
---

# Laws of booleans

There's many principal properties that hold for real numbers ($$\mathbb{R}$$) in math. You'll find that many hold for our boolean math as well. It's just 0's and 1's after all.

{% hint style="info" icon="user-question" %}
All of the laws have their form both in multiplication and addition forms. It might seem confusing at first, but you'll soon realize they both explain the same principle.
{% endhint %}

## Basic

<table><thead><tr><th width="137.5999755859375">Law</th><th width="231.39996337890625">Addition
(OR)</th><th width="184.2000732421875">Multiplication
(AND)</th><th width="140.7999267578125">Comment</th></tr></thead><tbody><tr><td><strong>Identity</strong></td><td><span class="math">a+0=a</span></td><td><span class="math">a\cdot1=a</span></td><td>Same as <span class="math">\mathbb{R}</span></td></tr><tr><td><strong>Null</strong></td><td><span class="math">a+1=1</span></td><td><span class="math">a\cdot0=0</span></td><td>Same as <span class="math">\mathbb{R}</span> <sup>(1)</sup></td></tr><tr><td><strong>Commutative</strong></td><td><span class="math">a+b=b+a</span></td><td><span class="math">a\cdot b=b\cdot a</span></td><td>Same as <span class="math">\mathbb{R}</span></td></tr><tr><td><strong>Associative</strong></td><td><span class="math">a+(b+c)=(a+b)c</span></td><td><span class="math">a(bc)=(ab)c</span></td><td>Same as <span class="math">\mathbb{R}</span></td></tr></tbody></table>

<sup>(1)</sup> As shown in [#why-does-1--1-1](0s-and-1s.md#why-does-1--1-1 "mention"), keep in mind that $$1+1=1$$ .

## Boolean basic

<table><thead><tr><th width="137.5999755859375">Law</th><th width="129">Addition (OR)</th><th width="149">Multiplication (AND)</th><th width="289.5999755859375">Comment</th></tr></thead><tbody><tr><td><strong>Idempotent</strong></td><td><span class="math">a+a=a</span></td><td><span class="math">a\cdot a=a</span></td><td>Comparing to itself is redundant</td></tr><tr><td><strong>Inverse</strong></td><td><span class="math">a+\overline a=1</span></td><td><span class="math">a\cdot \overline a=0</span></td><td>True OR not true = always<br>True AND not true = never</td></tr><tr><td><strong>Double negative</strong></td><td><span class="math">\overline{\overline{a}}=a</span></td><td></td><td>Self-explanatory</td></tr></tbody></table>

{% hint style="info" icon="lightbulb" %}
Try different values of 0's and 1's for each rule to better understand why it holds.
{% endhint %}



## Boolean advanced

<table><thead><tr><th width="142.39999389648438">Law</th><th width="260.5999755859375">Addition
(OR)</th><th width="233.40005493164062">Multiplication
(AND)</th></tr></thead><tbody><tr><td><strong>Distributive</strong></td><td><span class="math">a+bc=(a+b)(a+c)</span></td><td><span class="math">a(b+c)=ab+ac</span></td></tr><tr><td><strong>Absorption</strong></td><td><span class="math">a+ab=a</span></td><td><span class="math">a(a+b)=a</span></td></tr><tr><td><strong>De Morgan's</strong></td><td><span class="math">\overline{a+b}=\overline{a}\cdot\overline{b}</span></td><td><span class="math">\overline{ab}=\overline{a}+\overline{b}</span></td></tr></tbody></table>

{% hint style="info" icon="triangle-exclamation" %}
Make sure you understand De Morgan's law from this section and can apply it easily. It'll be used heavily in the next chapter if you wish to find the best solutions.
{% endhint %}

{% tabs %}
{% tab title="Distributive" %}
### **Distributive**

**Multiplication (AND):** Same as $$\mathbb{R}$$

**Addition (OR):** This law is not very intuitive at first sight. We will prove it backwards, starting from the right-hand side.

$$
(a+b)(a+c)\\
=aa + ac + ba + bc\\
=aa+ab+ac+bc\\
=~~a+ab+ac+bc\\
=~a(1+b+c)+bc\\
=a\cdot 1 +bc\\
=a+bc
$$

{% hint style="info" icon="user-question" %}
We used many of the laws described previously here, including the distributive law for multiplication.
{% endhint %}
{% endtab %}

{% tab title="Absorption" %}
### Absorption

You may think of this law as a special case of the **Distributive** law. However, knowing this law makes calculations faster.



**Addition (OR):** The idea is that the whole expression does not depend on $$ab$$, making it redundant.\
If $$a=0$$, then $$ab=0$$ anyway, since $$a$$ is zero. If $$a=1$$, then $$ab$$ doesn't matter since they're joined by $$+$$, making the expression true either way. For both cases of $$a$$, the expression evaluates to whatever $$a$$ is, making the term $$ab$$ redundant.

**Multiplication (AND):** The same line of reasoning applies, $$(a+b)$$ is redundant and does not affect the expression.\
\
**Alternatively,** if we use the **Distributive law**, for the multiplication form we get $$a(a+b)=aa+ab=a+ab$$, which gets us to the addition form; for the addition form, we have $$a+ab=a(1+b)=a\cdot1=a$$, which proves the law.



With the knowledge of this law, you may notice the proof for the **Distributive law** presented earlier could be simplified by absorbing the middle terms:<br>

$$
(a+b)(a+c)\\
=\bold{a+ac}+ba+bc\\
=\bold{a+ba}+bc\\
=a+bc
$$
{% endtab %}

{% tab title="De Morgan's" %}
### De Morgan's

Simply said, if we want to negate a bracket, we can separate the terms, negate each and flip the operation between them (addition becomes multiplication, and vice-versa).<br>

For simplicity "them" refers to the letters $$a,~b$$.

**Addition (OR):** Logically, if it's false that any of them are true, then all of them must be false.

**Multiplication (AND):** Logically, if it's false that all of them are true, then at least one of them must be false.

A mathematical proof for this can be found at [GeeksForGeeks - Proof of De Morgan's laws in boolean algebra](https://www.geeksforgeeks.org/engineering-mathematics/proof-of-de-morgans-laws-in-boolean-algebra/).
{% endtab %}
{% endtabs %}

## Practice

It's understandable that you will not remember all the laws by heart after reading three huge tables on this page. However, with applying logic and a little practice, you'll find basic boolean algebra is quick to learn.&#x20;

MIT offers an excellent set of practice problems, which can be found by [**clicking here.**](https://web.mit.edu/6.111/www/s2007/PSETS/pset1.pdf) The relevant sections are the very first 27 problems, and **Problem #3** (De Morgan's Theorem). Especially De Morgan will be used extensively later, so I recommend working out at least one of the exercises.

Solutions are provided for the first 27 problems at the end of the PDF. For De Morgan (Problem #3), you can find them below:

<details>

<summary>De Morgan's Theorem: Problem 3-1</summary>

$$~~~~~\overline{\overline{(a+d)}\cdot\overline{(\overline{b}+c)}}$$

$$=\overline{\overline{(a+d)}}+\overline{\overline{(\overline{b}+c)}}$$     _(De Morgan)_

$$=(a+d)+(\overline{b}+c)$$     _(Double negative)_

$$=a+\overline{b}+c+d$$           _(Associative law)_

</details>

<details>

<summary>De Morgan's Theorem: Problem 3-2</summary>

$$\over$$$$~~~~~\overline{\overline{a\cdot b\cdot \overline{c}}+\overline{(\overline{c}\cdot d)}}$$

$$=\overline{\overline{(a\cdot b\cdot \overline{c})}}\cdot\overline{\overline{(\overline{c}\cdot d)}}$$    _(De Morgan)_

$$=(a\cdot b\cdot\overline{c})\cdot (\overline{c}\cdot d)$$    _(Double negative)_

$$=a\cdot b\cdot\overline{c}\cdot\overline{c}\cdot d$$           _(Associative law)_

$$=a\cdot b\cdot\overline{c}\cdot d$$                _(Idempotent law)_

</details>

<details>

<summary>De Morgan's Theorem: Problem 3-2</summary>

$$\over$$$$~~~\overline{\overline{a}+d}\cdot\overline{b+\overline{c}}\cdot\overline{\overline{c}+d}$$

$$=(\overline{\overline{a}}\cdot\overline{d})\cdot\overline{b+\overline{c}}\cdot\overline{\overline{c}+d}$$         _(De Morgan)_

$$=(\overline{\overline{a}}\cdot\overline{d})\cdot(\overline{b}\cdot\overline{\overline{c}})\cdot(\overline{\overline{c}}\cdot\overline{d})$$       _(De Morgan x2)_

$$=(a\cdot\overline{d})\cdot(\overline{b}\cdot c)\cdot(c\cdot\overline{d})$$       _(Double negative)_

$$=a\cdot\overline{d}\cdot\overline{b}\cdot c\cdot c\cdot \overline{d}$$                 _(Commutative law - rearrangee)_

$$=a\cdot\overline{b}\cdot c\cdot\overline{d}$$                           _(Idempotent law)_

</details>
