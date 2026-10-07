---
description: What a chip...
icon: book-bookmark
---

# Theory

I strongly recommend reading through the explanation and specification of the ALU found in the original Tetris2NAND PDF, section 2.2.2.

This section will be split into exercises where we build the building blocks individually, starting with manipulating x, y and ending with putting it all together.

## How to test my sub-solutions?

In the IDE editor, click the yellow :file\_folder: icon, right next to where you execute your tests. Select `ALU-basic.tst` - this excludes the `ng` and `zr` flags for now.&#x20;

For each exercise, instead of clicking :fast\_forward: to run all the tests, click :arrow\_right: to execute **one** test at a time. You can see the values of all your intermediate variables in the window on the right, as well as the inputs supplied to each test in the `Compare File`. This is very useful for debugging your logic.

Another option is to temporarily set whatever you want to see to the `out` variable, and look at the `Output File`. This will show the input values, but also show your `out` variable for each test.

## HDL Syntax

* You can use the `true` and `false` predefined variables which supply a one or a zero. Will adapt to any bit-size (meaning they can be considered 16-bit constant 1/0 if needed)
*   For any chip, if you only need certain digits of the output, you can specify them by slicing directly in the output argument. You can do slices multiple way into different variables. Example: you want the last digit of an output:<br>

    ```
    And16(a=a, b=b, out[0]=lastdigit, out=out, out=fullout);
    ```
*   Once you assign something to `out` as an output variable, you can't reuse it right away. A workaround is to assign it again to an internal variable. Example:<br>

    ```
    And16(a=a, b=b, out=out, out=fullout);
    ```

    \
    Now you may use `fullout` as you wish, and your output pin will also contain the output value.
* You can redirect output (the last two bullet points) as many ways as you wish.
