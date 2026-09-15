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

<sup>(1)</sup> As shown in [#why-does-1--1-1](0s-and-1s.md#why-does-1--1-1 "mention"), keep in mind that $$1+1=1$$&#x20;

## Boolean basic

<table><thead><tr><th width="137.5999755859375">Law</th><th width="129">Addition (OR)</th><th width="149">Multiplication (AND)</th><th width="289.5999755859375">Comment</th></tr></thead><tbody><tr><td><strong>Idempotent</strong></td><td><span class="math">a+a=a</span></td><td><span class="math">a\cdot a=a</span></td><td>Comparing to itself is redundant</td></tr><tr><td><strong>Inverse</strong></td><td><span class="math">a+\overline a=1</span></td><td><span class="math">a\cdot \overline a=0</span></td><td>True OR not true = always<br>True AND not true = never</td></tr><tr><td><strong>Double negative</strong></td><td><span class="math">\overline{\overline{a}}=a</span></td><td></td><td>Self-explanatory</td></tr></tbody></table>

{% hint style="info" icon="lightbulb" %}
Try different values of 0's and 1's for each rule to better understand why it holds.
{% endhint %}



## Boolean advanced

<table><thead><tr><th width="142.39999389648438">Law</th><th width="260.5999755859375">Addition
(OR)</th><th width="233.40005493164062">Multiplication
(AND)</th></tr></thead><tbody><tr><td><strong>Distributive</strong></td><td><span class="math">a+bc=(a+b)(a+c)</span></td><td><span class="math">a(b+c)=ab+ac</span></td></tr><tr><td><strong>Absorption</strong></td><td><span class="math">a+ab=a</span></td><td><span class="math">a(a+b)=a</span></td></tr><tr><td><strong>De Morgan's</strong></td><td><span class="math">\overline{a+b}=\overline{a}\cdot\overline{b}</span></td><td><span class="math">\overline{ab}=\overline{a}+\overline{b}</span></td></tr></tbody></table>

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
If $$a=0$$, then $$ab=0$$ anyway, since $$a$$ is zero. If $$a=1$$, then $$ab$$ doesn't matter since                         they're joined by $$+$$, making the expression true either way. For both cases of $$a$$, the expression evaluates to whatever $$a$$ is, making the term $$ab$$ redundant.

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



