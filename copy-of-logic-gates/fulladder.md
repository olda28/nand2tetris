---
description: These chips are really growing on me.
icon: clone-plus
---

# FullAdder

_Note: I'm using \[C instead of output "carry"] and \[S instead of output "sum"]._

## Expected functionality

<div data-with-frame="true"><figure><img src=".gitbook/assets/image (40).png" alt=""><figcaption><p><a href="https://www.falstad.com/s.php?s=ejbN63"><em><strong>Click here for the interactive version</strong></em></a></p></figcaption></figure></div>

This chip adds **three** bits together. The function of this chip corresponds to the next steps in long addition - right-to-left. At each "full add", there's a potential carry from the neighboring column on the right, so you're potentially adding **three** numbers in total.

## Definition

```
IN a, b, c;  // 1-bit inputs
OUT S,     // Right bit of a + b + c
    C;   // Left bit of a + b + c
```

Add $$a,b,c$$ mathematically, outputting the $$S$$ (sum to write down, and the potential $$C$$ (carry) to remember for the next column of addition.

Start by making a truth table, and then implement the chip.

<details>

<summary>Truth table (simple)</summary>

<table data-search="false"><thead><tr><th width="50.39996337890625">a</th><th width="44.60003662109375">b</th><th width="49.199951171875">c</th><th width="77.40008544921875">sum</th><th width="89.59991455078125">carry</th></tr></thead><tbody><tr><td>0</td><td>0</td><td>0</td><td>0</td><td>0</td></tr><tr><td>0</td><td>1</td><td>0</td><td>1</td><td>0</td></tr><tr><td>1</td><td>0</td><td>0</td><td>1</td><td>0</td></tr><tr><td>1</td><td>1</td><td>0</td><td>0</td><td>1</td></tr><tr><td>0</td><td>0</td><td>1</td><td>1</td><td>0</td></tr><tr><td>0</td><td>1</td><td>1</td><td>0</td><td>1</td></tr><tr><td>1</td><td>0</td><td>1</td><td>0</td><td>1</td></tr><tr><td>1</td><td>1</td><td>1</td><td>1</td><td>1</td></tr></tbody></table>

Seems this problem is quite unique. See the next hint if you're unsure what to do next.

</details>

<details>

<summary>Hint #2</summary>

Reuse your components! You just built a HalfAdder. Try to apply it to two of the three inputs. Write it down in a truth table.

</details>

<details>

<summary>Hint #3</summary>

$$\text{HalfAdder}(a,b)\rightarrow s_0, c_0$$

Compare the columns. Which two of them seem similar?

</details>

<details>

<summary>Hint #4</summary>

<table data-search="false"><thead><tr><th width="49.2000732421875">c</th><th width="48.20001220703125">s0</th><th width="77.40008544921875">S</th></tr></thead><tbody><tr><td>0</td><td>0</td><td>0</td></tr><tr><td>0</td><td>1</td><td>1</td></tr><tr><td>0</td><td>1</td><td>1</td></tr><tr><td>0</td><td>0</td><td>0</td></tr><tr><td>1</td><td>0</td><td>1</td></tr><tr><td>1</td><td>1</td><td>0</td></tr><tr><td>1</td><td>1</td><td>0</td></tr><tr><td>1</td><td>0</td><td>1</td></tr></tbody></table>

Write a formula for $$S$$ with $$c$$ and $$s_0$$.

</details>

<details>

<summary>Hint #5</summary>

$$S=\overline{c}s_0+c\overline{s_0}$$

What does this pattern remind you of?

</details>

<details>

<summary>Hint #5</summary>

$$S=\text{XOR}(c,s_0)$$

Now, remember your HalfAdder. What is actually $$s_0$$ by definition?

</details>

<details>

<summary>Definition: S</summary>

_Notation:_ $$\text{XOR}(a,b)=a\oplus b$$

$$S=a\oplus b\oplus c$$

Two XOR gates. 8 NANDs. Don't use the built-in XOR, use the one you built yourself.

Tip: The best solution uses 9 NANDs total.

</details>

<details>

<summary>Hint #7</summary>

Now you need to focus on finding $$C$$. Truth tables, everyone.&#x20;

</details>

<details>

<summary>Hint #8</summary>

<table data-search="false"><thead><tr><th width="47.19989013671875">a</th><th width="44.60003662109375">b</th><th width="75.5999755859375">c</th><th width="89.59991455078125">C</th></tr></thead><tbody><tr><td>0</td><td>0</td><td>0</td><td>0</td></tr><tr><td>0</td><td>1</td><td>0</td><td>0</td></tr><tr><td>1</td><td>0</td><td>0</td><td>0</td></tr><tr><td>1</td><td>1</td><td>0</td><td>1</td></tr><tr><td>0</td><td>0</td><td>1</td><td>0</td></tr><tr><td>0</td><td>1</td><td>1</td><td>1</td></tr><tr><td>1</td><td>0</td><td>1</td><td>1</td></tr><tr><td>1</td><td>1</td><td>1</td><td>1</td></tr></tbody></table>

Find a formula for $$C$$ when $$c=0$$ and when $$c=1$$.

</details>

<details>

<summary>Hint #9</summary>

$$c=0\rightarrow C=a\cdot b$$

$$c=1\rightarrow C=a+b$$

This one is not as simple. Write down the formula into one line. Then, look at your two XOR gates - which one of those expressions do you already have?

</details>

<details>

<summary>Hint #10</summary>

$$C=\overline{c}(ab)+c(a+b)$$

If only we could express both $$ab$$ and $$a+b$$ using some shared variable. Your two XOR gates already have $$ab$$ easily if you apply NOT to the first NAND of your first XOR gate (essentially a HalfAdder). Try to transform it into $$a+b$$. Using something you also already have.&#x20;

This one is difficult. Try to find it yourself.&#x20;

</details>

<details>

<summary>Hint #11</summary>

Let's write down all the intermediate variables we already have from two XOR gates.

$$ab,\overline{ab},\overline{ab}b,\overline{ab}a,\overline{a}b+a\overline{b}$$

We're trying to get $$a+b$$ from $$ab$$ .

Using $$ab$$ and one of the intermediate values, try to find a formula for $$a+b$$.

</details>

<details>

<summary>Hint #12</summary>

$$ab+(\overline{a}b+a\overline{b})$$

What does that simplify to?

</details>

<details>

<summary>Hint #13</summary>

$$ab+(\overline{a}b+a\overline{b})$$

$$=a(b+\overline{b})+\overline{a}b$$

$$=a+\overline{a}b$$&#x20;

$$=\overline{\overline{a}\cdot\overline{\overline{a}b}}$$

$$=\overline{\overline{a}\cdot(a+\overline{b})}$$

$$=\overline{\overline{a}a+\overline{a}\overline{b}}$$

$$=\overline{\overline{a}\overline{b}}$$

$$=a+b$$

You could've skipped the last few steps if you recognize the absorption logic in $$a+\overline{a}b$$.

Remember that $$\overline{a}b+a\overline{b}=s_0$$. Just so that we don't have to keep writing it out.&#x20;

Now, knowing how to express $$a+b$$ using $$ab$$ and $$s_0$$, simplify the formula for $$C$$ from [#hint-10](fulladder.md#hint-10 "mention").

</details>

<details>

<summary>Hint #14</summary>

For readability, $$x=ab$$.

$$C=\overline{c}(x)+c(x+s_0)$$

Now simplify this.

</details>

<details>

<summary>Hint #15</summary>

$$C=\overline{c}x+cx+cs_0$$

$$C=x(\overline{c}+c)+cs_0$$

$$C=x+cs_0$$

Remember: we have only 1 NAND left to do this operation. Reduce the expression to a single NAND.

</details>

<details>

<summary>Hint #16</summary>

Think De Morgan.

</details>

<details>

<summary>Hint #17</summary>

$$C=\overline{\overline{x}\cdot \overline{cs_0}}$$

$$C=\overline{\overline{ab}\cdot\overline{cs_0}}$$

That's a single NAND. Look at your two XOR gates. Where can you find $$\overline{ab}$$ and $$\overline{cs_0}$$ in your gates? You've almost cracked it.&#x20;

</details>

<details>

<summary>Hint #18</summary>

$$\overline{ab}$$ is the very first NAND of the first XOR gate. \
Since $$s_0$$ is the output of the first XOR gate, we can find $$\overline{cs_0}$$ in the very first NAND of the second XOR gate. Assign some variables and implement your gate.

That's it. Good job.

</details>

<details>

<summary>Hint #19</summary>

You may have found yourself to have 10 NANDs despite following the hints if your first XOR gate is a HalfAdder and your second is pure XOR. Write your code anyway. Look at which statement is useless - you don't use the output.&#x20;

</details>

<details>

<summary>Best Solution (9 NANDs)</summary>

Two XOR gates (each 4 NANDs) and a single NAND to calculate $$C$$. In total, 9 NANDs.

```
CHIP FullAdder {
    IN a, b, c;  // 1-bit inputs
    OUT sum,     // Right bit of a + b + c
        carry;   // Left bit of a + b + c

    PARTS:
    // First XOR - variables x1, y01, y02, ab
    Nand(a=a, b=b, out=x1);
    Nand(a=a, b=x1, out=y01);
    Nand(a=x1, b=b, out=y02);
    Nand(a=y01, b=y02, out=ab);

    // Second XOR - variables x2, y11, y12, S
    Nand(a=ab, b=c, out=x2);
    Nand(a=ab, b=x2, out=y11);
    Nand(a=x2, b=c, out=y12);
    Nand(a=y11, b=y12, out=sum);

    // Final NAND - C
    Nand(a=x1, b=x2, out=carry);
}
```

<div data-with-frame="true"><figure><img src=".gitbook/assets/image (42).png" alt=""><figcaption><p><a href="https://www.falstad.com/s.php?s=jkD9By"><em><strong>Click here for the interactive version</strong></em></a></p></figcaption></figure></div>

</details>
