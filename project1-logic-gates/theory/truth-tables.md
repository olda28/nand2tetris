---
description: Numbers can't lie, right?
icon: table-list
---

# Truth tables

Let's assign a letter to another expression so we don't have to type it out every time.

<p align="center"><span class="math">x=a+\overline b</span></p>

\
Now, let's see what $$x$$ becomes for different values of $$a,~b$$.

<table><thead><tr><th width="54.5999755859375" data-type="number">a</th><th width="58" data-type="number">b</th><th width="56.20001220703125" data-type="number">x</th><th width="280.39996337890625">(calculation)</th></tr></thead><tbody><tr><td>0</td><td>0</td><td>1</td><td><span class="math">a+\overline b=0+\overline 0=0+1=1</span></td></tr><tr><td>0</td><td>1</td><td>0</td><td><span class="math">a+\overline b=0+\overline 1=0+0=0</span></td></tr><tr><td>1</td><td>0</td><td>1</td><td><span class="math">...=1+1=1</span></td></tr><tr><td>1</td><td>1</td><td>1</td><td><span class="math">...=1+0=1</span></td></tr></tbody></table>

This is called a **truth table**. It's a table where you fill in all the possible combinations of values for your inputs (the variables in your expression), and then the resulting expression(s) for each combination. For two variables, you'll have 4 rows, for three variables, it'll be 8 rows, and so on. It's all powers of 2.
