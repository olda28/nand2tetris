---
description: Multiplex or demultiplex. It's the same. Just backwards.
icon: split
---

# DMUX4Way

## Wait, why not DMUX4Way16?

You may have noticed we only implemented MUX16 and not even DMUX16 in the previous section. Why? Simply, for this project, we only need to select between single bits. A multi-wa DMUX just allows to split into multiple outputs. The input and outputs are still just a single bit. Be happy! Less tedious work for you.

## Expected functionality

<div data-with-frame="true"><figure><img src="../../copy-of-logic-gates/logic-gates/.gitbook/assets/image (31).png" alt=""><figcaption><p><a href="https://www.falstad.com/s.php?s=eo8td4"><em><strong>Click here for the interactive version</strong></em></a></p></figcaption></figure></div>

## Definition

```
IN in, sel[2];
OUT a, b, c, d;

[a, b, c, d] = [in, 0, 0, 0] if sel = 00
               [0, in, 0, 0] if sel = 01
               [0, 0, in, 0] if sel = 10
               [0, 0, 0, in] if sel = 11
```

Split the input to one of the outputs according to DMUX logic.

## Implementation

<details>

<summary>Hint #1</summary>

I know it's been a while back, but look at [dmux.md](../chips/dmux.md "mention"). This is the same, but scaled up to 4-way instead of the original 2-way. Same logic as with scaling MUX.

</details>

<details>

<summary>Hint #2</summary>

I'm really just repeating myself here - it's all analogous to multi-way mux. Look at the selector value. Chop it up into two blocks. Then join them. 3 DMUXs.

</details>

<details>

<summary>Hint #3</summary>

Chop it up, this time chopping the selector first by the first digit, then by the second digit. You know, like MUX - but the other way.

</details>

<details>

<summary>Hint #4</summary>

Put your `in` into a single DMux with the first digit of the selector. You get outputs $$ab$$ and $$cd$$ which contain your `in` assigned either to $$a,b$$ or $$c,d$$ in each of those two blocks. Now do it again, with the second digit of the selector, to choose between one of the two in the respective blocks.&#x20;

Really, you have just split the problem into two simple DMUX problems.&#x20;

</details>

<details>

<summary>Solution</summary>

Again, you can compare both to multi-way MUX and 2-way DMUX. It's all a scaled up analogy.

```
CHIP DMux4Way {
    IN in, sel[2];
    OUT a, b, c, d;

    PARTS:
    DMux(in=in, sel=sel[1], a=ab, b=cd);
    DMux(in=ab, sel=sel[0], a=a, b=b);
    DMux(in=cd, sel=sel[0], a=c, b=d);
}
```

<div data-with-frame="true"><figure><img src="../../copy-of-logic-gates/logic-gates/.gitbook/assets/image (32).png" alt=""><figcaption><p><a href="https://www.falstad.com/s.php?s=DPbUEc"><em><strong>Click here for the interactive version</strong></em></a></p></figcaption></figure></div>

</details>
