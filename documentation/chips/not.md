---
description: Keep it simple
icon: xmark-large
---

# NOT

## Expected functionality

<div data-with-frame="true"><figure><img src="../../copy-of-logic-gates/logic-gates/.gitbook/assets/image (4).png" alt=""><figcaption><p><a href="https://www.falstad.com/s.php?s=un5zPd"><em><strong>Click here for the interactive version</strong></em></a></p></figcaption></figure></div>

## Definition

```
if (in) out = 0, else out = 1
```

#### $$\text{NOT}(a)=\overline{a}$$

<table><thead><tr><th width="63.199981689453125">a</th><th width="123.79995727539062">NOT(a)</th></tr></thead><tbody><tr><td>0</td><td>1</td></tr><tr><td>0</td><td>1</td></tr><tr><td>1</td><td>0</td></tr><tr><td>1</td><td>0</td></tr></tbody></table>

## Implementation

<details>

<summary>Hint #1</summary>

Given we receive only one input, and we have only one operation available: NAND, there's not that many things you can do with it.

</details>

<details>

<summary>Solution (1 NAND)</summary>

```vhdl
CHIP Not {
    IN in;
    OUT out;

    PARTS:
    Nand(a=in, b=in, out=out);
}
```

<div data-with-frame="true"><figure><img src="../../copy-of-logic-gates/logic-gates/.gitbook/assets/image (3).png" alt=""><figcaption><p><a href="https://www.falstad.com/s.php?s=2TrVqR"><em><strong>Click here for the interactive version</strong></em></a></p></figcaption></figure></div>

</details>
