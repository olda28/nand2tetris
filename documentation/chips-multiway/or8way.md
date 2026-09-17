---
description: One is all it takes.
icon: square-xmark
---

# OR8Way



## Definition

```
IN in[8];
OUT out;

out = in[0] Or in[1] Or ... Or in[7]
```

Apply the OR gate between all of the elements in the array and produce a single-bit output.

## Implementation

<details>

<summary>Hint #1</summary>

Think about the Associative rule. We want to implement this:

```
out = in[0] + in[1] + in[2] + in[3] + ...
```

Chop it up. Chop chop. Think forks.

</details>

<details>

<summary>Solution (sequential)</summary>

```
CHIP Or8Way {
    IN in[8];
    OUT out;

    PARTS:
    Or(a=in[0], b=in[1], out=or1);
    Or(a=or1, b=in[2], out=or2);
    Or(a=or2, b=in[3], out=or3);
    Or(a=or3, b=in[4], out=or4);
    Or(a=or4, b=in[5], out=or5);
    Or(a=or5, b=in[6], out=or6);
    Or(a=or6, b=in[7], out=out);
}
```

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (12).png" alt="" width="563"><figcaption><p><a href="https://www.falstad.com/s.php?s=pTZwZU"><strong>Click here for the interactive version</strong></a></p></figcaption></figure></div>

While this works, and is as efficient, I recommend looking at the "forks" solution below. It'll make the next few gates much easier to think about.

</details>

<details>

<summary>Solution (forks)</summary>

```vhdl
CHIP Or8Way {
    IN in[8];
    OUT out;

    PARTS:
    Or(a=in[0], b=in[1], out=or01);
    Or(a=in[2], b=in[3], out=or23);
    Or(a=in[4], b=in[5], out=or45);
    Or(a=in[6], b=in[7], out=or67);

    Or(a=or01, b=or23, out=or0123);
    Or(a=or45, b=or67, out=or4567);

    Or(a=or0123, b=or4567, out=out);
}
```

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (13).png" alt="" width="375"><figcaption><p><a href="https://www.falstad.com/s.php?s=80vEw9"><strong>Click here for the interactive version</strong></a></p></figcaption></figure></div>

</details>
