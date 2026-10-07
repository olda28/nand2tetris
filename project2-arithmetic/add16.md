---
description: Almost like a human!
icon: plus-large
---

# Add16

_Note: I'm using \[C instead of output "carry"] and \[S instead of output "sum"]._

_Note: Remember, arrays are indexed from the back (right-to-left)._

## Expected functionality

<div data-with-frame="true"><figure><img src=".gitbook/assets/image (43).png" alt=""><figcaption><p><a href="https://www.falstad.com/s.php?s=JX2WAD"><em><strong>Click here for the interactive version</strong></em></a></p></figcaption></figure></div>

This chip adds two 16-bit (16-digit) numbers, ignoring the final carry and outputs the sum as a 16-bit number.

## Definition

```
16-bit adder: Adds two 16-bit two's complement values.
The most significant carry bit is ignored.

IN a[16], b[16];
OUT out[16];
```

<details>

<summary>Hint #1</summary>

You've just built two chips - one that adds two numbers, and one that adds three numbers. Think about how you would proceed if you were to add two 16-digit numbers using long addition on paper. Right-to-left.

</details>

<details>

<summary>Hint #2</summary>

Lots of copy pasting. Good thing you built your adders. Isn't it convenient now that in HDL, arrays are indexed from the back?

</details>

<details>

<summary>Solution</summary>

Half-adder to add the right-most digit (`a[0] + b[0]`) since we have no carry. Full-adders for the rest (`a[1..15] + b[1..15]` since we might have a third number as carry.

```
HIP Add16 {
    IN a[16], b[16];
    OUT out[16];

    PARTS:
    HalfAdder(a=a[0], b=b[0], sum=out[0], carry=c0);
    FullAdder(a=a[1], b=b[1], c=c0, sum=out[1], carry=c1);
    FullAdder(a=a[2], b=b[2], c=c1, sum=out[2], carry=c2);
    FullAdder(a=a[3], b=b[3], c=c2, sum=out[3], carry=c3);
    FullAdder(a=a[4], b=b[4], c=c3, sum=out[4], carry=c4);
    FullAdder(a=a[5], b=b[5], c=c4, sum=out[5], carry=c5);
    FullAdder(a=a[6], b=b[6], c=c5, sum=out[6], carry=c6);
    FullAdder(a=a[7], b=b[7], c=c6, sum=out[7], carry=c7);
    FullAdder(a=a[8], b=b[8], c=c7, sum=out[8], carry=c8);
    FullAdder(a=a[9], b=b[9], c=c8, sum=out[9], carry=c9);
    FullAdder(a=a[10], b=b[10], c=c9, sum=out[10], carry=c10);
    FullAdder(a=a[11], b=b[11], c=c10, sum=out[11], carry=c11);
    FullAdder(a=a[12], b=b[12], c=c11, sum=out[12], carry=c12);
    FullAdder(a=a[13], b=b[13], c=c12, sum=out[13], carry=c13);
    FullAdder(a=a[14], b=b[14], c=c13, sum=out[14], carry=c14);
    FullAdder(a=a[15], b=b[15], c=c14, sum=out[15], carry=c15);
}
```

_I've decided not to provide a solution diagram as 1 HalfAdder and 15 FullAdder would take quite a lot of space, and since the solution is trivial._&#x20;

</details>
