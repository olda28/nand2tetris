---
description: A cherry on top of all the hard work.
icon: square-minus
---

# ng

## Definition

```hdl
if (out < 0)  equals 1, else 0
```

<details>

<summary>Hint #1</summary>

Reuse your variables. Look at the last exercise.

</details>

<details>

<summary>Hint #2</summary>

Two's complement. Again, look at the last exercise.&#x20;

</details>

<details>

<summary>Hint #3</summary>

You only really need to modify the output slicing in your "no" section. You already have a variable that says if your output is negative.

</details>

<details>

<summary>Solution</summary>

```
// From your "no" section
Mux16(..., out[15]=firstdigit, out[15]=ng);
```

If the first digit is negative, the number is negative. That's all there is to it.&#x20;

</details>
