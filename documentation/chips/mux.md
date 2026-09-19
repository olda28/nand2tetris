---
description: MUltipleXor - pick one!
icon: merge
---

# MUX

_Note: I personally use "z" instead of "sel" as it's shorter and easier to work with._

## Expected functionality

_Note: in this image, a and b are flipped as opposed to the previous diagrams._&#x20;

<div data-with-frame="true"><figure><img src="../../copy-of-logic-gates/logic-gates/.gitbook/assets/image (11).png" alt=""><figcaption><p><a href="https://www.falstad.com/s.php?s=fr65dT"><em><strong>Click here for the interactive version</strong></em></a></p></figcaption></figure></div>

## Definition

```
if (z = 0) out = a, else out = b
```

#### _You will need to derive the formula yourself as it's not trivial._

## Implementation

<details>

<summary>Truth table</summary>

<table data-search="false"><thead><tr><th width="63.199981689453125">a</th><th width="55.39996337890625">b</th><th width="63.199951171875">z</th><th width="123.79995727539062">MUX(a,b,z)</th></tr></thead><tbody><tr><td>0</td><td>0</td><td>0</td><td>0</td></tr><tr><td>0</td><td>1</td><td>0</td><td>0</td></tr><tr><td>1</td><td>0</td><td>0</td><td>1</td></tr><tr><td>1</td><td>1</td><td>0</td><td>1</td></tr><tr><td>0</td><td>0</td><td>1</td><td>0</td></tr><tr><td>0</td><td>1</td><td>1</td><td>1</td></tr><tr><td>1</td><td>0</td><td>1</td><td>0</td></tr><tr><td>1</td><td>1</td><td>1</td><td>1</td></tr></tbody></table>

Can you find the algebraic function definition now?

</details>

<details>

<summary>Formula</summary>

If z = 0, then a will be on the first term.\
If z = 1, then b will be on the first term.\
We join them with OR as we want either value, since z=0 and z=1 cannot be true at the same time (AND would not make sense)

$$\text{MUX}(a,b,z)=\overline{z}a+zb$$

Now try to NANDify it.

</details>

<details>

<summary>Hint #1</summary>

There's this mathematician that had a useful law named after him. Can't remember. [#boolean-advanced](../theory/laws-of-booleans.md#boolean-advanced "mention")?

</details>

<details>

<summary>Solution (4 NANDs)</summary>

$$x=\text{NAND}(b,z)\\y=\text{NAND}(a,\overline{z})$$

$$\overline{z}=\text{NOT}(z)$$

$$\text{MUX}(a,b,z)=\text{NAND}(x,y)$$

```
CHIP Mux {
    IN a, b, sel; // sel = z
    OUT out;

    PARTS:
    Nand(a=b, b=sel, out=x);

    Not(in=sel, out=notz);
    Nand(a=a , b=notz, out=y);

    Nand(a=x, b=y, out=out);
}
```

<div data-with-frame="true"><figure><img src="../../copy-of-logic-gates/logic-gates/.gitbook/assets/image (25).png" alt=""><figcaption><p><a href="https://www.falstad.com/s.php?s=vOTxm4"><em><strong>Click here for the interactive version</strong></em></a></p></figcaption></figure></div>

</details>
