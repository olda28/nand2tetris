---
description: First step towards addition.
icon: square-plus
---

# HalfAdder

## Expected functionality

<div data-with-frame="true"><figure><img src=".gitbook/assets/image (39).png" alt=""><figcaption><p><a href="https://www.falstad.com/s.php?s=nTjocU"><em><strong>Click here for the interactive version</strong></em></a></p></figcaption></figure></div>

This chip adds two bits together. The function of this chip corresponds to the first step in long addition - the rightmost number. There's no carry, so you're adding two numbers in total.

## Definition

```
IN a, b;    // 1-bit inputs
OUT sum,    // Right bit of a + b 
    carry;  // Left bit of a + b
```

Add $$a$$ and $$b$$ mathematically, outputting the $$sum$$ to write down, and the potential $$carry$$ to remember for the next column of addition.

Start by making a truth table, and then implement the chip.

<details>

<summary>Truth table</summary>

<table><thead><tr><th width="50.39996337890625">a</th><th width="44.60003662109375">b</th><th width="77.40008544921875">sum</th><th width="89.59991455078125">carry</th></tr></thead><tbody><tr><td>0</td><td>0</td><td>0</td><td>0</td></tr><tr><td>0</td><td>1</td><td>1</td><td>0</td></tr><tr><td>1</td><td>0</td><td>1</td><td>0</td></tr><tr><td>1</td><td>1</td><td>0</td><td>1</td></tr></tbody></table>

Now try to extract the formula for each of the output variables.

</details>

<details>

<summary>Formula</summary>

$$sum=\text{XOR}(a,b)$$

$$carry=\text{AND}(a,b)$$

</details>

<details>

<summary>Simple Solution (6 NANDs)</summary>

```
CHIP HalfAdder {
    IN a, b;    // 1-bit inputs
    OUT sum,    // Right bit of a + b 
        carry;  // Left bit of a + b

    PARTS:
    And(a=a, b=b, out=carry);
    Xor(a=a, b=b, out=sum);
}
```

<div data-with-frame="true"><figure><img src=".gitbook/assets/image (36).png" alt=""><figcaption><p><a href="https://www.falstad.com/s.php?s=DPbUEc"><em><strong>Click here for the interactive version</strong></em></a></p></figcaption></figure></div>

</details>

<details>

<summary>Best hint #1</summary>

Look at the diagrams or code solutions of both XOR and AND. Is there an operation they both do, that we could reuse?

</details>

<details>

<summary>Best Solution (5 NANDs)</summary>

They both share the variable $$x=\text{NAND}(a,b)$$ .

It's a matter of copy pasting the rest of the definitions of AND and XOR, while sharing this first step in your code.

```
CHIP HalfAdder {
    IN a, b;    // 1-bit inputs
    OUT sum,    // Right bit of a + b 
        carry;  // Left bit of a + b

    PARTS:
    Nand(a=a, b=b, out=x);

    // Nand + Not => And
    Not(in=x, out=carry);

    // Nand + ... => Xor
    Nand(a=x, b=b, out=y1);
    Nand(a=a, b=x, out=y2);
    Nand(a=y1, b=y2, out=sum);
}
```

<div data-with-frame="true"><figure><img src=".gitbook/assets/image (38).png" alt=""><figcaption><p><a href="https://www.falstad.com/s.php?s=1VRYmE"><em><strong>Click here for the interactive version</strong></em></a></p></figcaption></figure></div>

</details>
