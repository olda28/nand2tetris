---
description: Reuse your components!
icon: merge
---

# MUX4Way16

## HDL Syntax

_Note: in HDL, arrays are indexed from the back._\
_If `sel=110` , then `sel[0]=0, sel[1]=1, sel[2]=1` ._

_**To slice a part of an array (from `i` to `j` including):**_ `arr[i..j]`

## Expected functionality

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (19).png" alt=""><figcaption><p><a href="https://www.falstad.com/s.php?s=97vcvW"><em><strong>Click here for the interactive version</strong></em></a></p></figcaption></figure></div>

## Definition

```
IN a[16], b[16], c[16], d[16],
   sel[2];
OUT out[16];

out = a if sel = 00
      b if sel = 01
      c if sel = 10
      d if sel = 11
```

Apply MUX to the 16-bit arrays, outputting one of the arrays based on the selector.

## Implementation

<details>

<summary>Hint #1</summary>

Chop this up into steps, as done previously. Make use of your previously built MUX16. Remind yourself what it does.

You can get only a part of the selector:\
**1st digit:** `sel[1]` \
**2nd digit:** `sel[0]`

</details>

<details>

<summary>Hint #2</summary>

First, apply MUX16 to the first half. Then, another one to the second half. Choose the selector digits to help you do this.

</details>

<details>

<summary>Hint #3</summary>

Multiplex (with MUX16) the arrays $$a$$ and $$b$$ based on the second digit of the selector. Do the same for the arrays $$c$$ and $$d$$ .

The first digit of the selector tells you whether to choose between the $$a,~b$$ or $$c,~d$$ arrays. The second tells you which of those two to select then.

Remember, arrays are indexed from the back.

</details>

<details>

<summary>Hint #3</summary>

```
Mux16(a=a, b=b, sel=sel[0], out=ab);
Mux16(a=c, b=d, sel=sel[0], out=cd);
```

Now you have an array called $$ab$$ which contains either $$a$$ or $$b$$ according to the input. An an array called $$cd$$ which contains either $$c$$ or $$d$$ .

Now join them according to the first digit of the selector.

</details>

<details>

<summary>Solution (sequential)</summary>

```
CHIP Mux4Way16 {
    IN a[16], b[16], c[16], d[16], sel[2];
    OUT out[16];
    
    PARTS:
    Mux16(a=a, b=b, sel=sel[0], out=ab);
    Mux16(a=c, b=d, sel=sel[0], out=cd);
    Mux16(a=ab, b=cd, sel=sel[1], out=out);
}
```

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (21).png" alt=""><figcaption><p><a href="https://www.falstad.com/s.php?s=BIE1ts"><em><strong>Click here for the interactive version</strong></em></a></p></figcaption></figure></div>

</details>
