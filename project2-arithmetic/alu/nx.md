---
description: This one's easier, I promise
icon: circle-exclamation
---

# nx

## Definition

```hdl
// if (nx == 1) sets x = !x       // bitwise not
```

<details>

<summary>Hint #1</summary>

This is really simple if you followed the last exercise. You have a selector, a useful chip and `zxdone` from the last step.

</details>

<details>

<summary>Hint #2</summary>

Use MUX16 again.&#x20;

</details>

<details>

<summary>Solution</summary>

Use Not16 to create the inverse. Then select between it, and the non-inversed array using Mux16 with nx as the selector.

```
Not16(in=zxdone, out=antizxdone);
Mux16(a=zxdone, b=antizxdone, sel=nx, out=xdone);
```

</details>
