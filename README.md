# Project 1 README

Student: Victoria Ramos (920012149)

## Project Status
'Gray' is complete and 'FiveSeven' is in progress.

## Known Issues


## References
* [Build an XOR gate from AND/NOT](https://electronics.stackexchange.com/questions/487529/build-an-xor-gate-from-and-not)
* [Some other link](https://stackoverflow.com)

* [Karnaugh map | Boolean Function Simplification] (https://youtu.be/Ev4rRI_jcK0?si=bKejVnqtfPNiKB2W)
  

## Generative AI Use
I used ChatGPT for Prompt 1, and ChatGPT for Prompt 2....

### Prompt 1
How do you create an XOR from only and/or/not gates?

### Response 1
To create an XOR (exclusive OR) gate using only AND, OR, and NOT gates, you can follow these steps. The XOR gate outputs true only when the inputs are different.

The truth table for XOR is:

| A | B | A XOR B |
|---|---|---------|
| 0 | 0 |    0    |
| 0 | 1 |    1    |
| 1 | 0 |    1    |
| 1 | 1 |    0    |

The Boolean expression for XOR can be derived as:\
A &oplus; B = (A &and; &not; B) &or; (&not; A &and; B)

This can be broken down into the following steps:

1. Create \(&not; A\) and \(&not; B\) using NOT gates.
1. Create \(A &and; &not; B\) and \(&not; A &and; B\) using AND gates.
1. Combine the results of the two AND gates using an OR gate.

Here is the step-by-step logic construction:

1. **NOT gates** to get \(&not; A\) and \(&not; B\):\
   NOT(A) &rarr; &not; A\
   NOT(B) &rarr; &not; B

1. **AND gates** to get \(A &and; &not; B\) and \(&not; A &and; B\):\
   A &and; &not; B &rarr; AND(A, &not; B)\
   &not; A &and; B &rarr; AND(&not; A, B)

1. **OR gate** to get the final result:\
   (A &and; &not; B) &or; (&not; A &and; B) &rarr; OR(AND(A, &not; B), AND(&not; A, B))

Putting it all together in a circuit diagram:

1. Input \(A\) goes to a NOT gate to produce \(&not; A\).
1. Input \(B\) goes to a NOT gate to produce \(&not; B\).
1. Input \(A\) and the output of the NOT gate for \(B\) go to an AND gate to produce \(A &and; &not; B\).
1. Input \(B\) and the output of the NOT gate for \(A\) go to an AND gate to produce \(&not; A &and; B\).
1. The outputs of the two AND gates go to an OR gate to produce the final output \(A &oplus; B\).

In terms of Boolean logic:\
XOR(A, B) = \(A &and; &not; B\) &or; \(&not; A &and; B\) 

This way, you have constructed an XOR gate using only AND, OR, and NOT gates.

### Changes 1
I needed XNOR, so changed it to:\
&not;\(\(A &and; &not; B\) &or; \(&not; A &and; B\)\)

### Prompt 2
What are some tips for grouping the 1s in the k-map and simplifying the boolean expression?

### Response 2
When you’re grouping 1s in a K-map, the goal is to make the **fewest, largest power-of-two groups possible** so you get the simplest Boolean expression.
Here are the key tips:

Only Group in Powers of 2
* Groups can have **1, 2, 4, 8, or 16 cells** — no other sizes.
* Each group must be **rectangular** (including squares) and contain only 1s.

Make Groups as Large as Possible
* Bigger groups → fewer variables in the term.
* Example:
  * Group of 8 → 1 variable remains.
  * Group of 4 → 2 variables remain.
  * Group of 2 → 3 variables remain.
  * Group of 1 → all variables remain (least simplified).

Groups Can Overlap
* Overlapping is allowed (and often necessary) to cover all 1s with the largest groups.
* The same 1 can belong to more than one group if it helps simplify.

Use Wrap-Around Adjacency
* The left and right edges of the K-map are adjacent.
* The top and bottom edges are adjacent.
* This lets you form larger wrap-around groups.

Minimize the Number of Groups**
* Cover all 1s with the **fewest groups** while keeping groups as large as possible.
* Start grouping with the largest clusters, then move to smaller leftover ones.

Each Group Gives a Term

For SOP (Sum of Products):
  * Identify which variables are **constant** in the group.
  * If a variable is 1 in all cells → keep it as itself (A).
  * If a variable is 0 in all cells → keep it as its complement ($\overline{A}$).
  * If it changes within the group → eliminate it from that term.

Double-Check for Redundancy
* If removing a group still covers all 1s, it’s redundant — delete it.

✅ **Example:**
If a group of 4 covers cells where $A=1$ and $B$ changes but $C=0$ in all cases → the term is $A\overline{C}$.


### Changes 2
I figured that I hadn't derived the correct boolean equations and I needed a quick refresher on k-maps. After getting some tips and watching the youtube video (linked in references), I had to re-do my boolean expressions and I now have a better understanding of grouping the 1s. 
I specifically changed
* $G1 = \overline{B2}(B1+B0)+\overline{B3}B2\overline{B1}\overline{B0}$ to $G1 = \overline{B2}(B0+B1)+B2\overline{B0}\overline{B1}$
* $G2 = (\overline{B3}B2)+(B3\overline{B2}$) to $G2 = (\overline{B3}(B2+B0B1)+B3\overline{B2}(\overline{B0}+\overline{B1}$)
