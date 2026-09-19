---
description: The easiest finish line yet!
icon: split
---

# DMUX8Way

## Expected functionality

<div data-with-frame="true"><figure><img src="../../copy-of-logic-gates/logic-gates/.gitbook/assets/image (35).png" alt=""><figcaption><p><a href="https://www.falstad.com/s.php?s=lmQJLJ"><em><strong>Click here for the interactive version</strong></em></a></p></figcaption></figure></div>

## Definition

```
IN in, sel[3];
OUT a, b, c, d, e, f, g, h;

[a, b, c, d, e, f, g, h] = [in, 0,  0,  0,  0,  0,  0,  0] if sel = 000
                           [0, in,  0,  0,  0,  0,  0,  0] if sel = 001
                           [0,  0, in,  0,  0,  0,  0,  0] if sel = 010
                           [0,  0,  0, in,  0,  0,  0,  0] if sel = 011
                           [0,  0,  0,  0, in,  0,  0,  0] if sel = 100
                           [0,  0,  0,  0,  0, in,  0,  0] if sel = 101
                           [0,  0,  0,  0,  0,  0, in,  0] if sel = 110
                           [0,  0,  0,  0,  0,  0,  0, in] if sel = 111
```

Split the input to one of the outputs according to DMUX logic.

## Implementation

<details>

<summary>Hint #1</summary>

You already have a chip to DMUX an input 4 ways. This requires 8 ways. If only there was a way to select one of two outputs based on an input variable. To demultiplex, so to say.

</details>

<details>

<summary>Hint #2</summary>

Look at the first digit of the selector. Now split the options into two large 4-way blocks. Now, well, 4-way DMUX them each time.

</details>

<details>

<summary>Hint #3</summary>

Apply 2-way (simple) DMUX to `in` based on the first digit of the selector. Now, you need to DMUX those two blocks 4-ways, twice. You have a chip for that.&#x20;

</details>

<details>

<summary>Hint #6</summary>

Put your `in` into a single DMUX with the first digit of the selector. You get outputs $$abcd$$ and $$efgh$$ which contain your `in` assigned either to $$a,b,c,d$$ or $$e,f,g,h$$ in each of those two blocks. Now do it again, with the last two digits of the selector, to choose between one of the four in the respective blocks.&#x20;

Really, you have just split the problem into two simple DMUX4Way problems.&#x20;

</details>

<details>

<summary>Solution</summary>

Once again, you can compare it to the 4-way DMUX. It's all just scaled up.

```
CHIP DMux8Way {
    IN in, sel[3];
    OUT a, b, c, d, e, f, g, h;

    PARTS:
    DMux(in=in, sel=sel[2], a=abcd, b=efgh);
    DMux4Way(in=abcd, sel=sel[0..1], a=a, b=b, c=c, d=d);
    DMux4Way(in=efgh, sel=sel[0..1], a=e, b=f, c=g, d=h);
}
```

<div data-with-frame="true"><figure><img src="../../copy-of-logic-gates/logic-gates/.gitbook/assets/image (34).png" alt=""><figcaption><p><a href="https://www.falstad.com/s.php?s=8raE1A"><em><strong>Click here for the interactive version</strong></em></a></p></figcaption></figure></div>

</details>
