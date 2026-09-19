---
description: DeMUltipleXor - split them!
icon: split
---

# DMUX

_Note: I personally use \["z" instead of "sel"] and \["d" instead of "in"] as it's shorter and easier to work with._

## Expected functionality

<div data-with-frame="true"><figure><img src="../../copy-of-logic-gates/logic-gates/.gitbook/assets/image (26).png" alt=""><figcaption><p><a href="https://www.falstad.com/s.php?s=axmdaS"><em><strong>Click here for the interactive version</strong></em></a></p></figcaption></figure></div>

## Definition

```
IN in, sel; // in = d, sel = z
OUT a, b;

[a, b] = [d, 0] if z = 0
         [0, d] if z = 1
```

#### _You will need to derive the formula yourself as it's not trivial._

## Multiple outputs?

The demultiplexor, as the name hints, splits one input into multiple outputs. It may seem daunting at first, but simply try to find a solution to $$\text{DMUX}(d,z)\rightarrow a$$ and  $$\text{DMUX}(d,z)\rightarrow b$$ . Based on the two inputs $$d$$ and $$z$$, set $$a$$ and set $$b$$.

In other words, the original definition below can be thought of as&#x20;

```
a = d, b = 0  if z = 0
a = 0, b = d  if z = 1
```

## Implementation

Once again, there's a simple 5 NANDs solution, and then a beautiful 4 NAND solution.

<details>

<summary>I'm not sure what to do first</summary>

If you're still confused by the multiple outputs, build Truth tables with columns: $$d$$, $$z$$, $$a$$ and $$d$$, $$z$$, $$b$$. You may also build just one with $$d$$, $$z$$, $$a$$, $$b$$, to be concise.

</details>

<details>

<summary>Truth table</summary>

<table data-search="false"><thead><tr><th width="63.199981689453125">d</th><th width="55.39996337890625">z</th><th width="63.199951171875">a</th><th width="123.79995727539062">b</th></tr></thead><tbody><tr><td>0</td><td>0</td><td>0</td><td>0</td></tr><tr><td>0</td><td>1</td><td>0</td><td>0</td></tr><tr><td>1</td><td>0</td><td>1</td><td>0</td></tr><tr><td>1</td><td>1</td><td>0</td><td>1</td></tr></tbody></table>

Now look at the relevant columns and find the formulas for $$a$$ and $$b$$ separately.&#x20;

$$a=~?$$

$$b=~?$$

</details>

<details>

<summary>Formulas</summary>

$$a=1$$ only when $$d=1$$ while $$z=0$$.\
$$a=d\overline{z}$$

$$b=1$$ only when $$d=1$$ while $$z=1$$.\
$$b=dz$$

You know the "simple" solution has 5 NANDs. There's two different outputs needed. \
\
One variable's solution will use 2 NANDs.\
The other variable's solution will use 3 NANDs.

</details>

<details>

<summary>Simple Hint #1</summary>

You have two available inputs: $$d$$ and $$z$$, and you need to create

1. $$d\overline{z}$$
2. $$dz$$

You don't have many NANDs to spare. There's not that many combinations. Give it a shot.

</details>

<details>

<summary>Simple Hint #2</summary>

The most simple idea is the correct one here. Simply NAND the two variables.

$$x=\text{NAND}(d,\overline{z})$$

$$y=\text{NAND}(d,z)$$

Can you take it from here?

</details>

<details>

<summary>Simple Hint #3</summary>

Keep it simple.

$$x = \overline{d\overline{z}}$$

$$y = \overline{dz}$$

How do you get to $$a=d\overline{z}$$ using one operation on $$x$$?\
How do you get to $$b=dz$$ the same way with $$y$$?

</details>

<details>

<summary>Simple Solution (5 NANDs)</summary>

$$x=\text{NAND}(d,\overline{z})\\y=\text{NAND}(d,z)$$

$$\overline{z}=\text{NOT}(z)$$

$$a=\text{NOT}(x)\\b=\text{NOT}(y)$$

```hdl
CHIP DMux {
    IN in, sel; // in = d, sel = z
    OUT a, b;

    PARTS:
    Not(in=sel, out=notz);

    Nand(a=in, b=notz, out=x);
    Nand(a=in, b=sel, out=y);

    Not(in=x, out=a);
    Not(in=y, out=b);
}
```

<div data-with-frame="true"><figure><img src="../../copy-of-logic-gates/logic-gates/.gitbook/assets/image (27).png" alt=""><figcaption><p><a href="https://www.falstad.com/s.php?s=PcNybF"><em><strong>Click here for the interactive version</strong></em></a></p></figcaption></figure></div>

$$\text{NAND}(d,z)$$ gives us the inverse of our wanted $$b$$ expression. $$a$$ is the same, except we waste a NAND on negating $$z$$ first.\
\
There's an extremely elegant but hard to spot implementation that does not waste this extra NAND. Dare to find it?

</details>

<details>

<summary><strong>Best solution - starter</strong></summary>

So you dare! If you're not sure where to start, let's write down what we know in an organized way.

**Target output:**

$$a=d\overline{z}\\b=dz$$

**Target variables:**

$$x=\overline{d\overline{z}}\\y=\overline{dz}$$

The variables $$x,~y$$ are the same as in the simple solution. Two negations at the end, and two NANDs to get to $$x,y$$ from $$d,z$$.\
In total: 4 NANDs.

The issue is the extra negation of $$z$$ before doing all of that. That makes it 5 NANDs.

The task is simple yet tricky: _how can we get_ $$x$$ _using only one NAND, instead of two?_

</details>

<details>

<summary>Best Hint #1</summary>

We know the transformation from $$b$$ to $$y$$ is the shortest it can be. So let's define ourselves $$y$$ first.

Single operation. Three available variables. You're close.

</details>

<details>

<summary>Best Hint #2</summary>

Obviously the mentioned operation is NAND. The three variables mentioned are $$d,~z,~y$$.

Try out the combinations. Think De Morgan. Get to that $$x$$.

</details>

<details>

<summary>Best Hint #3</summary>

The hint about defining $$y$$ first was not for nothing.

$$\text{NAND}(y,?)=x$$

Now just put it **all** together. 2 NANDs, 2 NOTs.

</details>

<details>

<summary>Best Solution (4 NANDs)</summary>

If you found the solution, good work! The missing piece is:

$$x=\text{NAND}(y,d)$$   <sub>_(explanation at the bottom)_</sub>

Then, the solution is the same as the simple one. Putting it together:

$$y=\text{NAND}(d,z)\\x=\text{NAND}(y,d)$$

$$a=\text{NOT}(x)\\b=\text{NOT}(y)$$

```
CHIP DMux {
    IN in, sel; // in = d, sel = z
    OUT a, b;

    PARTS:
    Nand(a=in, b=sel, out=y); // y = !(dz)
    Nand(a=in, b=y, out=x); // x = !(d!z) = !(yd)
    
    Not(in=x, out=a); // a = !x
    Not(in=y, out=b); // b = !y
}
```

<div data-with-frame="true"><figure><img src="../../copy-of-logic-gates/logic-gates/.gitbook/assets/image (28).png" alt=""><figcaption><p><a href="https://www.falstad.com/s.php?s=EW71rd"><em><strong>Click here for the interactive version</strong></em></a></p></figcaption></figure></div>

### Why does $$x=\text{NAND}(y,d)$$?

Here's the mathematical derivation:

$$\text{NAND}(y,d)=\overline{yd}=\overline{\overline{dz}d}$$&#x20;

$$=\overline{(\overline{d}+\overline{z})d}$$    _(De Morgan)_

$$=\overline{\overline{d}d+\overline{z}d}$$     _(distribute)_

$$=\overline{\overline{z}d}$$               _(null law)_

$$=x$$

Essentially, by NANDing an expression which has $$\overline{d}$$ with $$d$$, we make the $$\overline{d}$$ redundant, as it does not change the expression. It's similar to the principle of the absorption law.&#x20;

</details>
