---
description: A complicated start to a simple chip
icon: creative-commons-zero
---

# zx

## Definition

```hdl
if (zx == 1) sets x = 0        // 16-bit constant
```

<details>

<summary>Hint #1</summary>

Check [theory.md](theory.md "mention") > HDL Syntax. Don't we already have what we want? Just need to decide if we want it.

</details>

<details>

<summary>Hint #2</summary>

Well, one option is to keep x as-is. The other is to replace it by a zero constant. If only there were a chip that allows to select one of two options based on a selector (such as `zx` )

</details>

<details>

<summary>Solution</summary>

Use MUX16

```
Mux16(a=x, b=false, sel=zx, out=zxdone);
```

_Note: to check your work, set the `out` argument on the last line to `out` to see it in the output file. I won't repeat myself, remember this for the next exercises._

</details>
