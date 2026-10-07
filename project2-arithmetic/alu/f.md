---
description: Oh look, we didn't suffer through the adders for nothing!
icon: circle-plus
---

# f

## Definition

```hdl
// if (f == 1)  sets out = x + y  // integer 2's complement addition
// if (f == 0)  sets out = x & y  // bitwise and
```

<details>

<summary>Hint #1</summary>

This is easier than it looks. Clearly, there's two options based on a single-bit selector. I wonder if we have a chip for that (spoiler: we do)

</details>

<details>

<summary>Hint #2</summary>

Prepare the two options. Then use MUX16.

</details>

<details>

<summary>Solution</summary>

Prepare both of the options, and select the right one using MUX16.

```
And16(a=xdone, b=ydone, out=xANDy);
Add16(a=xdone, b=ydone, out=xADDy);
Mux16(a=xANDy, b=xADDy, sel=f, out=alldone);  
```

</details>
