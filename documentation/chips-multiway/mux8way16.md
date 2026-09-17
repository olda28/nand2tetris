---
description: Reuse your components (again)
icon: merge
---

# MUX8Way16

## HDL Syntax

_**To slice a part of an array (from `i` to `j` including):**_ `arr[i..j]` \\\
E.g. get `10` from `110` : `arr[0..1]` \
E.g. get `11` from `110` : `arr[1..2]`

## Expected functionality

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (24).png" alt=""><figcaption><p><a href="https://www.falstad.com/s.php?s=b5Jrzz"><em><strong>Click here for the interactive version</strong></em></a></p></figcaption></figure></div>

## Definition

```
IN a[16], b[16], c[16], d[16], e[16], f[16], g[16], h[16],
   sel[3];
OUT out[16];

out = a if sel = 000
      b if sel = 001
      c if sel = 010
      d if sel = 011
      e if sel = 100
      f if sel = 101
      g if sel = 110
      h if sel = 111
```

Apply MUX to the 16-bit arrays, outputting one of the arrays based on the selector.

## Implementation

<details>

<summary>Hint #1</summary>

This is really similar to the previous chip, except with more forks, since there's an extra selector bit. Look at the definition provided. How could you chop this up into half?

</details>

<details>

<summary>Hint #2</summary>

Make use of your MUX4Way16 chip. The solution is very similar. Chop it up into two blocks again. Only this time, they'll be twice as big.

The logic is the same as with MUX4Way16, just scaling up. Look at how you scaled MUX16 to MUX4Way16. Now scale MUX4Way16 to MUX8Way16 the same way.

</details>

<details>

<summary>Hint #3</summary>

Look at the selector value carefully.

```
000
001
010
011
100
101
110
111
```

Your MUX4Way16 chip takes a two bit selector `xx` and chooses between four 16-bit arrays. What two digits of the selector can you take to do that twice, and split the 8 options in two equally-sized blocks?

</details>

<details>

<summary>Hint #4</summary>

Multiplex (with MUX164Way16) the arrays $$a,b,c,d$$ based on the last two digits of the selector. Do the same for the arrays $$e,f,g,h$$ .

The last two digits tell you whether to choose between the $$a,b,c,d$$ or $$e,f,g,h$$ arrays. The first digit tells you which of those two to select then.

Remember, you can slice the array to your needs.

</details>

<details>

<summary>Hint #5</summary>

```
Mux164Way(a=a, b=b, c=c, d=d, sel=sel[0], out=abcd);
Mux164Way(a=e, b=f, c=g, d=h, sel=sel[0], out=efgh);
```

Now you have an array called $$abcd$$ which contains either $$a$$ or $$b$$ or $$c$$ or $$d$$ according to the input. And a second array with the same thing but with $$e,f,g,h$$ .

Now select the right one according to the first digit of the selector.

</details>

<details>

<summary>Hint #6</summary>

You have two 16-bit arrays. What function applies MUX to two 16-bit arrays based on a one-bit selector??

</details>

<details>

<summary>Solution</summary>

Compare this to the MUX4Way16 solution. You'll see the diagram and logic is almost identical, just scaled up.

```
CHIP Mux8Way16 {
    IN a[16], b[16], c[16], d[16],
       e[16], f[16], g[16], h[16],
       sel[3];
    OUT out[16];

    PARTS:
    Mux4Way16(a=a, b=b, c=c, d=d, sel=sel[0..1], out=abcd);
    Mux4Way16(a=e, b=f, c=g, d=h, sel=sel[0..1], out=efgh);
    Mux16(a=abcd, b=efgh, sel=sel[2], out=out);
}
```

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (30).png" alt=""><figcaption><p><a href="https://www.falstad.com/s.php?s=DPbUEc"><em><strong>Click here for the interactive version</strong></em></a></p></figcaption></figure></div>

</details>
