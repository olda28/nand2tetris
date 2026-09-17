---
description: Reduce, reduce, reduce.
icon: info
---

# Multi-way gates

The previous section was focused on performing an operation such as AND on two arrays of bits, outputting the same array with the operation applied to **each pair** of bits. What if we want to apply **one** operation to **all** of the bits?&#x20;

In other words, what if we have 4 bits, and we want to perform AND on **all of them**?&#x20;

Essentially instead of:\
$$x=\text{AND}(a,b)=a\cdot b$$\
we want this:\
&#x20;$$x=\text{AND}(a,b,c,d)=a\cdot b\cdot c\cdot d$$

That would be called a 4-way AND. In this sense, the basic operations we defined are only 2-way.&#x20;

Of course, writing $$\text{AND}(a,b,c,d,...)$$ would be tedious for a large number of bits. So we supply a single variable, which - you guessed it - is an array.

