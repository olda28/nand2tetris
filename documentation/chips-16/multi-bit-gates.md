---
description: All the same, just bigger
icon: info
---

# Multi-bit gates

Remember when we said boolean functions (gates, chips...) take in one or two inputs, and produce a single output?

That was not completely accurate. Insofar our variables were only a single bit: either a 0 or a 1. What if we want to input an array of bits? As you'll see, we can create an _n_-bit gate that performs its single-bit operation on each element of the array.

In programming terms, instead of a boolean variable, we receive an **array** of booleans. We loop over them, and perform the single-bit gate we implemented in the previous section.

For instance, a 16-bit NOT gate receives $$a$$ as an array of 16 bits. Instead of receiving $$a=1$$ or $$a=0$$, we receive for example $$a=[0,1,0,1,1,0,1]$$. The gate then loops over the items, one by one, and performs the basic NOT on them. The output will then be $$b=[1,0,1,0,0,1,0]$$.

This will be mostly very boring, as it's just copy pasting the one operation _n_-times, since the NAND2Tetris HDL doesn't support loops of any sort.

