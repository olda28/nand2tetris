---
description: Can't be any easier.
icon: seal-exclamation
---

# no

{% hint style="warning" %}
After finishing this exercise, your test script in the online IDE should pass green. Before clicking over to the next exercise, switch your test script in the IDE back to `ALU.tst` again.
{% endhint %}

## Definition

```hdl
// if (no == 1) sets out = !out   // bitwise not
```

<details>

<summary>Hint #1</summary>

You have a chip for this. Can't be any easier.

</details>

<details>

<summary>Solution</summary>

Prepare both of the options, and select the right one using MUX16.

```
Not16(in=alldone, out=antialldone);
Mux16(a=alldone, b=antialldone, sel=no, out=out);
```

</details>
