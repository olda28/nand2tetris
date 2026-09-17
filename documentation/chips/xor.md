---
description: eXclusive OR
icon: shield-plus
---

# XOR

## Expected functionality

<div data-with-frame="true"><figure><img src="/broken/files/3paukENhxpVpYeodkvb0" alt=""><figcaption><p><a href="https://www.falstad.com/s.php?s=5ruBos"><em><strong>Click here for the interactive version</strong></em></a></p></figcaption></figure></div>

## Definition

```
if ((a and Not(b)) or (Not(a) and b)) out = 1, else out = 0
```

#### $$XOR(a,b)=a\overline{b}+\overline{a}b$$

<table><thead><tr><th width="63.199981689453125">a</th><th width="55.39996337890625">b</th><th width="123.79995727539062">XOR(a,b)</th></tr></thead><tbody><tr><td>0</td><td>0</td><td>0</td></tr><tr><td>0</td><td>1</td><td>1</td></tr><tr><td>1</td><td>0</td><td>1</td></tr><tr><td>1</td><td>1</td><td>0</td></tr></tbody></table>

## Implementation

There is one simple implementation with 9 NANDs, and then the best one with 4 NANDs.

<details>

<summary>Simple Hint #1</summary>

Reuse your gates you just built! Look at the definition above and break it down.

</details>

<details>

<summary>Simple Hint #2</summary>

First you negate, then you AND. Do it again. Then you OR them together.

</details>

<details>

<summary>Simple Solution (9 NANDs)</summary>

$$x=\text{AND}(a,\overline{b})\\y=\text{AND}(\overline{a},b)$$

$$\overline{a}=\text{NOT}(a)\\\overline{b}=\text{NOT}(b)$$

$$\text{XOR}(a,b)=\text{OR}(x,y)$$

```
CHIP Xor {
    IN a, b;
    OUT out;

    PARTS:
    Not(in=b, out=notb);
    Not(in=a, out=nota);

    And(a=a, b=notb, out=x);
    And(a=nota, b=b, out=y);
    
    Or(a=x, b=y, out=out);
}
```

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption><p><a href="https://www.falstad.com/s.php?s=8MtZKX"><em><strong>Click here for the interactive version</strong></em></a></p></figcaption></figure></div>

</details>

<details>

<summary>Best Hint #1</summary>

It's all only NANDs. You have NAND and you have two input variables. Maybe more, if you chain them - experiment.

</details>

<details>

<summary>Best Hint #2</summary>

$$x=\text{NAND}(a,b)$$

Now you have three variables and NAND. Go on, try the combinations. Building truth tables for your experiments will help.

</details>

<details>

<summary>Best Hint #3</summary>

$$x=\text{NAND}(a,b)\\y_1=\text{NAND}(x, b)\\y_2=\text{NAND}(a,x)$$

You can NAND x with a or b again. The right thing is to do both. You're missing a single NAND - it's as simple as it looks.

</details>

<details>

<summary>Best Solution (4 NANDs)</summary>

The easiest way to find this solution is to just experiment, since the amount of combinations is small enough to find it eventually.

If you want, it's possible to find it algebraically - if you love De Morgan.\
\
$$x=\text{NAND}(a,b)\\y_1=\text{NAND}(x, b)\\y_2=\text{NAND}(a,x)$$

$$\text{XOR}(a,b)=\text{NAND}(y_1,y_2)$$

```
CHIP Xor {
    IN a, b;
    OUT out;

    PARTS:
    Nand(a=a, b=b, out=x);
    Nand(a=x, b=b, out=y1);
    Nand(a=a, b=x, out=y2);
    Nand(a=y1, b=y2, out=out);
}
```

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption><p><a href="https://www.falstad.com/s.php?s=I6kzhO"><em><strong>Click here for the interactive version</strong></em></a></p></figcaption></figure></div>

</details>

<details>

<summary>Best Solution - Algebraic derivation</summary>

<p align="center"><span class="math">\overline{a}b+a\overline{b}</span></p>

<p align="center"><span class="math">\overline{(\overline{\overline{a}b})(\overline{a\overline{b}})}</span></p>

<p align="center"><span class="math">\overline{(a+\overline{b})(\overline{a}+b)}</span></p>

<p align="center"><span class="math">\overline{a\overline{a}+ab+\overline{b}\overline{a}+\overline{b}b}</span></p>

<p align="center"><span class="math">\overline{ab+\overline{b}\overline{a}}</span><span class="math">\overline{}</span></p>

<p align="center"><span class="math">\overline{ab+(\overline{a+b})}</span></p>

<p align="center"><span class="math">(\overline{ab})(a+b)</span></p>

<p align="center"><span class="math">a\overline{ab}+\overline{ab}b</span></p>

<p align="center"><span class="math">\overline{(\overline{a\overline{ab}})(\overline{\overline{ab}b})}</span></p>

<p align="center">At this point it's visibly all NANDs. It's just rearranging with a lot of help with De Morgan's law.</p>

</details>
