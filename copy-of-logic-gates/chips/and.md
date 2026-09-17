---
description: Think negative
icon: ampersand
---

# AND

## Expected functionality

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption><p><a href="https://www.falstad.com/s.php?s=6PtHYW"><em><strong>Click here for the interactive version</strong></em></a></p></figcaption></figure></div>

## Definition

```
if (a and b) out = 1, else out = 0 
```

#### $$\text{AND}(a,b)=ab$$

<table><thead><tr><th width="63.199981689453125">a</th><th width="55.39996337890625">b</th><th width="123.79995727539062">AND(a,b)</th></tr></thead><tbody><tr><td>0</td><td>0</td><td>0</td></tr><tr><td>0</td><td>1</td><td>0</td></tr><tr><td>1</td><td>0</td><td>0</td></tr><tr><td>1</td><td>1</td><td>1</td></tr></tbody></table>

## Implementation

<details>

<summary>Hint #1</summary>

We have only two gates so far. Look at their definitions and truth tables.

</details>

<details>

<summary>Hint #2</summary>

What does a double-negative do in boolean algebra?

</details>

<details>

<summary>Solution (2 NANDs)</summary>

```
CHIP And {
    IN a, b;
    OUT out;
    
    PARTS:
    Nand(a=a, b=b, out=x);
    Not(in=x, out=out); // Nand(a=x, b=x, out=out);
}
```

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption><p><a href="https://www.falstad.com/s.php?s=3p1Euc"><em><strong>Click here for the interactive version</strong></em></a></p></figcaption></figure></div>

</details>
