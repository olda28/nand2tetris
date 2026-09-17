---
description: Not everyone has a breadboard at home.
icon: pencil-line
---

# Using the IDE

The [NAND2Tetris IDE](https://nand2tetris.github.io/web-ide/chip/) uses a HDL: "Hardware Description Language". It's a way to concisely define custom chips, using inputs, outputs and logic you'll implement yourself. It's like drawing electrical diagrams in physics, except you do it with text.

## Example

```
CHIP MyNAND {
    IN in;
    OUT out;

    PARTS:
    Nand(a=in, b=in, out=out);
}
```

`CHIP MyNAND {` : defines a custom chip/gate called MyNAND, that\
`IN x,y;`  takes two separate bits (1 or 0) as input, called `x` and `y`, and also\
`OUT out;`  one bit as output, called `out` .

`PARTS:` defines the section where your chip's logic will be

`Nand(a=x, b=y, out=out);` calls upon a predefined chip called `Nand`, supplying `x` and `y` as inputs, and telling the chip to assign the output to `out`. Every chip call must be ended with a `;`

We could then elsewhere call our custom chip like this:

```
CHIP AnotherChip {
   ...
   PARTS:
   Nand(x=..., y=..., out=...);
}
```

## Testing your new chip

Let's assume you've written your logic and everything, and you want to check if it does what it's supposed to.

You can do this by clicking the yellow :fast\_forward: button on the bottom of the IDE. If your chip is wrong, you'll get a red error text, if it's correct, you'll get a green text. You can check the **Compare File**, **Output File** and **Diff Table** to see what was expected and what your chip actually provided.&#x20;

Once you're happy, you can select the next chip to implement in the dropdown on the top of the page.

## In-built chips

In case you decide to skip a section (don't do that!), the IDE provides its own built-in definitions of chips. I recommend (as does the book) that you implement the chips in order, and reuse only the ones you've already built (and the provided NAND of course). A small hint for you though, you'll only use NAND (given) and NOT (built) in the **Basic Chips** section. Remember, it's all just NANDs.
