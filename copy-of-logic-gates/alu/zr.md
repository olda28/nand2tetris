---
description: An useful information I suppose.
icon: square-0
---

# zr

## Definition

```hdl
if (out == 0) zr = 1, else zr = 0
```

<details>

<summary>Hint #1</summary>

Make sure to read up on how two's complement works.

</details>

<details>

<summary>Hint #2</summary>

What dictates if a number is positive or negative in two's complement. What happens when the number inversed is zero?

</details>

<details>

<summary>Hint #3</summary>

If the first digit is 1, then the number is negative. If 0, then positive. Since zero doesn't have a negative, it stays the same - with a leading zero. Make use of that.

</details>

<details>

<summary>Hint #4</summary>

As found in the original book theory:&#x20;

> To obtain the code of $$-x$$ from the code of $$x$$, \[...] flip all the bits of x and add 1 to the result.

You have chips for that. Now, how will you know if the original number was zero?&#x20;

</details>

<details>

<summary>Hint #5</summary>

You can check if the original first digit is the same as the first digit after inverting.&#x20;

Tip: you can get the first digit by slicing as per [theory.md](theory.md "mention").&#x20;

How do you know if two bits are both zero?

</details>

<details>

<summary>Hint #6</summary>

```
// From your "no" section
 Mux16(..., out=out, out[0..15]=output, out[15]=firstdigit);
```

```
// In your "zr" section
...
Inc16(in=antiout, out[15]=firstinvdigit);
```

You can check if the original first digit is the same as the first digit after inverting.&#x20;

Tip: you can get the first digit by slicing as per [theory.md](theory.md "mention").&#x20;

How do you know if two bits are both zero?

</details>

<details>

<summary>Solution</summary>

NOR (Negation of OR) gives 1 only if both values are zero (or one, but that can't happen with what we're doing)

```
   // negate the bus (if first digit stays the same then zr=1)
Not16(in=output, out=antiout);
Inc16(in=antiout, out[15]=firstinvdigit);

   // NOR = true only if both are zero
Or(a=firstdigit, b=firstinvdigit, out=antizr);
Not(in=antizr, out=zr);
```

</details>
