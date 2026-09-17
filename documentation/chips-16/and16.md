---
description: Remember the arrays are aligned.
icon: square-ampersand
---

# AND16

## Definition

```
IN a[16], b[16];
OUT out[16];

for i = 0, ..., 15:
out[i] = a[i] And b[i] 
```

Apply $$\text{AND}$$ between the elements of arrays $$a$$ and $$b$$, and output a same-sized array of the result.

## Implementation

<details>

<summary>Hint #1</summary>

The solution is rather similar to the previous NOT16 gate. Except as with normal AND we have two inputs to work on, instead of just one. Remember the $$a$$ and $$b$$ arrays are the same length, and are aligned.&#x20;

Example:

```
 a  = [0,1,1,0,1,0,0,0,1,0,1,0,0,0,1,1]
 b  = [1,1,1,0,0,1,0,1,1,1,0,1,0,0,1,0]
out = AND16(a=a, b=b);
out = [0,1,1,0,0,0,0,0,1,0,0,0,0,0,1,0]
```

</details>

<details>

<summary>Solution</summary>

```vhdl
CHIP And16 {
    IN a[16], b[16];
    OUT out[16];

    PARTS:
    And(a=a[0], b=b[0], out=out[0]);
    And(a=a[1], b=b[1], out=out[1]);
    And(a=a[2], b=b[2], out=out[2]);
    And(a=a[3], b=b[3], out=out[3]);
    And(a=a[4], b=b[4], out=out[4]);
    And(a=a[5], b=b[5], out=out[5]);
    And(a=a[6], b=b[6], out=out[6]);
    And(a=a[7], b=b[7], out=out[7]);
    And(a=a[8], b=b[8], out=out[8]);
    And(a=a[9], b=b[9], out=out[9]);
    And(a=a[10], b=b[10], out=out[10]);
    And(a=a[11], b=b[11], out=out[11]);
    And(a=a[12], b=b[12], out=out[12]);
    And(a=a[13], b=b[13], out=out[13]);
    And(a=a[14], b=b[14], out=out[14]);
    And(a=a[15], b=b[15], out=out[15]);
}
```

</details>
