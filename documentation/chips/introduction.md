---
description: So, what next?
icon: info
---

# Introduction

Gates can also be called chips, which hints at their physical form in circuits. Your job, in this first project of NAND2Tetris is to implement the basic gates.

The recommended way to do that is in the [NAND2Tetris online IDE](https://nand2tetris.github.io/web-ide/chip/). From there, in the dropdown menu, select "Project 1", the chip you're working on and go to work.

Introduction to the HDL, as well as more information and context are available in the [original project PDF. ](https://www.nand2tetris.org/_files/ugd/44046b_f2c9e41f0b204a34ab78be0ae4953128.pdf) I provided a brief explanation on the next page, but I still recommend reading the original.

There are some tips for implementation, and a full list of the chips for this project in [another original PDF.](https://drive.google.com/open?id=17Rt3z7_OvpoQNlM6xtmC67Rn3blgM4W5\&authuser=schocken%40gmail.com\&usp=drive_fs)

This Gitbook is easier to follow if the original book is too much information or too difficult at times, but at the cost of leaving out a lot of background context and the depth of knowledge. If you have a lot of time, I heavily recommend reading the original PDFs/book as well. This Gitbook is more "let's go build", the original book is more "let's really understand and build".

## Interactive diagrams

Thanks to the wonderful Paul Falstad's circuit creator, there are interactive diagrams in most sections showing:

1. The expected functionality using a single predefined block for showcase.
2. The solution(s) implemented using NAND and/or other of your chips.&#x20;

Under each diagram image will be a clickable link for an interactive diagram.

You may click the numbers in the diagram to toggle boolean/digital values and see how the chip is supposed to work before implementing it yourself. (You may also right click the number, select "Edit..." and input your own value)

Arrays/buses are represented as a decimal number there. Nonetheless, the number behind `/` will tell you the length of the array. If you see a pin labeled `I1/16` it means it expects/outputs a 16-bit array. Have fun!
