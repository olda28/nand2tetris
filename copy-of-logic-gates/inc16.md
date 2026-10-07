---
description: Just a smidge.
icon: square-1
---

# Inc16

## HDL Syntax

If you need access to a constant zero or one, the variables `true` (1) and `false` (0) are defined in the IDE. They will fill any amount of bits with the value (any width).

_Note: Remember, arrays are indexed from the back (right-to-left)._

## Expected functionality

<div data-with-frame="true"><figure><img src=".gitbook/assets/image (44).png" alt=""><figcaption><p><a href="https://www.falstad.com/s.php?s=tKebOG"><em><strong>Click here for the interactive version</strong></em></a></p></figcaption></figure></div>

This chip adds one (1) to a 16-bit number. This will be useful later on.

## Definition

```
16-bit incrementer:
out = in + 1

IN in[16];
OUT out[16];
```

<details>

<summary>Hint #1</summary>

In which columns do you add the 1 if you were to write it down as long addition?

</details>

<details>

<summary>Hint #2</summary>

With what chip can you add two numbers at the right-most column? How many numbers will you need to be adding for the rest of the columns?

</details>

<details>

<summary>Solution</summary>

Start off the HalfAdder chain with adding `true` and `in[0]` for the right-most digit. Add up the carry and the next number for the rest.

```
CHIP Inc16 {
    IN in[16];
    OUT out[16];

    PARTS:
    HalfAdder(a=in[0], b=true, sum=out[0], carry=c0);
    HalfAdder(a=in[1], b=c0, sum=out[1], carry=c1);
    HalfAdder(a=in[2], b=c1, sum=out[2], carry=c2);
    HalfAdder(a=in[3], b=c2, sum=out[3], carry=c3);
    HalfAdder(a=in[4], b=c3, sum=out[4], carry=c4);
    HalfAdder(a=in[5], b=c4, sum=out[5], carry=c5);
    HalfAdder(a=in[6], b=c5, sum=out[6], carry=c6);
    HalfAdder(a=in[7], b=c6, sum=out[7], carry=c7);
    HalfAdder(a=in[8], b=c7, sum=out[8], carry=c8);
    HalfAdder(a=in[9], b=c8, sum=out[9], carry=c9);
    HalfAdder(a=in[10], b=c9, sum=out[10], carry=c10);
    HalfAdder(a=in[11], b=c10, sum=out[11], carry=c11);
    HalfAdder(a=in[12], b=c11, sum=out[12], carry=c12);
    HalfAdder(a=in[13], b=c12, sum=out[13], carry=c13);
    HalfAdder(a=in[14], b=c13, sum=out[14], carry=c14);
    HalfAdder(a=in[15], b=c14, sum=out[15], carry=c15);
}
```

_I've decided not to provide a solution diagram as 16 HalfAdders would take quite a lot of space considering the solution is trivial._&#x20;

</details>
