---
description: THE building block
icon: circle-ampersand
---

# NAND

NAND means Not-And, aka $$\text{NOT}(\text{AND}(a,b))$$ . This means to apply the function AND, and negate the output. This chip has a specific diagram.&#x20;

<figure><img src="https://i.redd.it/how-does-the-two-following-images-make-sense-together-nand-v0-n9ucytsp21yb1.png?width=362&#x26;format=png&#x26;auto=webp&#x26;s=2bf8deaa26e337da19bf4a6c1c077be491ca825a" alt=""><figcaption></figcaption></figure>

## Why NAND?

The gates NAND and NOR have the interesting property that ALL other gates can be derived from them, by interconnecting multiple NAND chips. This is the basic idea behind the NAND2Tetris project.&#x20;

## Expected functionality

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption><p><a href="https://www.falstad.com/s.php?s=iPhq2j"><em><strong>Click here for the interactive version</strong></em></a></p></figcaption></figure></div>

## Definition

#### $$\text{NAND}(a,b)=\overline{ab}$$

<table><thead><tr><th width="63.199981689453125">a</th><th width="64.60003662109375">b</th><th width="123.79995727539062">NAND(a,b)</th></tr></thead><tbody><tr><td>0</td><td>0</td><td>1</td></tr><tr><td>0</td><td>1</td><td>1</td></tr><tr><td>1</td><td>0</td><td>1</td></tr><tr><td>1</td><td>1</td><td>0</td></tr></tbody></table>

## Implementation

This chip is provided and thus there is no need to implement it yourself. Onto the next one!
