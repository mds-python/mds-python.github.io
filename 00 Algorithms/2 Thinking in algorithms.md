# Thinking in algorithms

An important factor of computer programs written in a formal language is the fact that it must be inhumanly precise. Imagine, you ask someone ‘*Please close the window.*’ If there are two windows in the room and only one of them is open, the person will guess you are asking to close the window, which is open. However, computer executing your program is not so clever! Instead, you must give a set of formal instructions:

1. Walk to the *first window*.
2. If the *first window* is open, close the *first window*.
3. Walk to the *second window*.
4. If the *second window* is open, close the *second window*.

Splitting a single task of closing a window into a sequence of more precise instructions is called a **top-down** approach to problems. Here, we will analyze more problems this way. In order to focus on operations and not the notation, we will not use formal language. However, we will stick to one simple rule: **don't use prepositions**. Notice that in the above example we did not use the preposition ‘*it*’, using explicit names *first window*. and *second window* instead. If we need to operate on some data that we do not know at the moment of writing an algorithm (which is more common than not), we still use **labels**.

To illustrate this, let's write a top down algorithm that computes the area of a rectangle. To do so, we need to identify what data we need at the beginning (our **input**) and what result should be produced (what is the **output** of the algorithm).

![Rectangle a b](rectangle.png)

```
INPUT:
  a — rectangle width
  b — rectangle height

STEPS:
  1. Compute a×b and name the result ‘area’.

OUTPUT:
  area
```

As you can see, we have used **labels** `a` and `b` for an input data that <u>needs to be provided at the program execution</u> ( at the moment, let's do not worry how) and also we have performed some computations and **labeled** (named) their result as `area`. Finally, we can provide this named value as the algorithm output.

Let's take a look at another example. Given two numbers *x*<sub>1</sub> and *x*<sub>2</sub> computer their average. The algorithm would be as follows:

```
INPUT:
  x₁, x₂ — given numbers

STEPS:
  — Compute x₁ + x₂ and name the result ‘total’.
  — Compute ‘average’ as total / 2.

OUTPUT:
  average
```

What you see above is a recipe. It contains two simple steps. You should try to track it and see how the labeled values change:

| STEP                                         | *x*<sub>1</sub> | *x*<sub>2</sub> | *total* | *average* | RESULT |
| -------------------------------------------- | --------------- | --------------- | ------- | --------- | ------ |
| **INPUT**                                    | **2**           | **4**           |         |           |        |
| *total* = *x*<sub>1</sub> + *x*<sub>2</sub>. | 2               | 4               | 6       |           |        |
| *average* = *total* / 2.                     | 2               | 4               | 6       | 3         |        |
| **OUTPUT**                                   | 2               | 4               | 6       | 3         | **3**  |

Now, something more complicated: given two numbers, tell what is the value of the larger ones:

```
INPUT:
  x₁, x₂ — given numbers

STEPS:
  — If x₁ > x₂, set value of x to ‘larger’.
    Else, let ‘larger’ be x₂.

OUTPUT:
  larger
```

Let's track it for some sample data:

| STEP                                          | *x*<sub>1</sub> | *x*<sub>2</sub> | *larger* | RESULT |
| --------------------------------------------- | --------------- | --------------- | -------- | ------ |
| **INPUT**                                     | **2**           | **1**           |          |        |
| Checking if *x*<sub>1</sub> > *x*<sub>2</sub> | 2               | 1               |          | yes    |
| *larger* = *x*<sub>1</sub>                    | 2               | 1               | 2        |        |
| **OUTPUT**                                    | 2               | 1               | 2        | **2**  |

How will it look for some different data?

| STEP                                          | *x*<sub>1</sub> | *x*<sub>2</sub> | *larger* | RESULT |
| --------------------------------------------- | --------------- | --------------- | -------- | ------ |
| **INPUT**                                     | **2**           | **3**           |          |        |
| Checking if *x*<sub>1</sub> > *x*<sub>2</sub> | 2               | 3               |          | no     |
| *larger* = *x*<sub>2</sub>                    | 2               | 3               | 3        |        |
| **OUTPUT**                                    | 2               | 3               | 3        | **3**  |

The above algorithm was not performed linearly. Depending on some condition either one or another operation was performed. This is called a *conditional*.

Let's take a look at more advanced example — solution to [Quadratic equation](https://en.wikipedia.org/wiki/Quadratic_equation) of the form *a* *x*<sup>2</sup> + *b* *x* + *c* = 0. I hope you remember how to do it! Hence, the simplest and most naive algorithm would be:

```bash
INPUT:
  a, b, c — equation coefficients.

STEPS:
  — Compute Δ = b² - 4×a×c
  — Compute first solution x₁ = (-b - √Δ) / (2×a)  # remember about computation order rules
  — Compute second solution x₂ = (-b + √Δ) / (2×a) # and use parentheses as necessary

OUTPUT:
  x₁, x₂
```

Text after `#` is just a comment, not a part of algorithm.

If we are interested in complex solution is any case, this is (almost) sufficient. However, if we want only real solutions, we must remember that their existence depends on the value od *Δ*. So we must use conditionals:

```
INPUT:
  a, b, c — equation coefficients.

STEPS:
  — Compute Δ = b² - 4×a×c
  — If Δ > 0 do the following:
    │ — Compute first solution x₁ = (-b - √Δ) / (2×a)
    │ — Compute second solution x₂ = (-b + √Δ) / (2×a)
    Else if Δ = 0:
    │ — Compute the only solution -b / (2×a) and name it ‘x₁’ for consistency
    │ — The second solution (x₂) does not exits
    If neither of the above is true (because Δ < 0), then:
    │ — Neither x₁ nor x₂ exist

OUTPUT:
  x₁, x₂
```

Above, you can see that the algorithm can take three paths, depending on the value of *Δ*. What is important, is that in each path we mention both *x*<sub>1</sub> and *x*<sub>2</sub>. This is because, we have identified both of them as an output, so **we must define such names in every possible path!** Even in the cases when one or both of them does not exits, we mark them as non-existent (right now, you need not worry how: programming languages allow to do it one way or another).

So the algorithm looks good... Let's track if for some data:

Solving *x*<sup>2</sup> + 2 *x* – 8 = 0:

| STEP                                      | *a*   | *b*   | *c*    | *Δ* | *x*<sub>1</sub> | *x*<sub>2</sub> | RESULT        |
| ----------------------------------------- | ----- | ----- | ------ | --- | --------------- | --------------- | ------------- |
| **INPUT**                                 | **1** | **2** | **-8** |     |                 |                 |               |
| *Δ* = *b*<sup>2</sup> – 4×*a*×*c*         | 1     | 2     | -8     | 36  |                 |                 |               |
| Checking if *Δ* > 0                       | 1     | 2     | -8     | 36  |                 |                 | yes           |
| *x*<sub>1</sub> = (–*b* – √*Δ*) / (2×*a*) | 1     | 2     | -8     | 36  | -4              |                 |               |
| *x*<sub>2</sub> = (–*b* + √*Δ*) / (2×*a*) | 1     | 2     | -8     | 36  | -4              | 2               |               |
| **OUTPUT**                                | 1     | 2     | -8     | 36  | -4              | 2               | **-4**, **2** |

Solving *x*<sup>2</sup> – 2 *x* + 1 = 0:

| STEP                              | *a*   | *b*    | *c*   | *Δ* | *x*<sub>1</sub> | *x*<sub>2</sub> | RESULT           |
| --------------------------------- | ----- | ------ | ----- | --- | --------------- | --------------- | ---------------- |
| **INPUT**                         | **1** | **-2** | **1** |     |                 |                 |                  |
| *Δ* = *b*<sup>2</sup> – 4×*a*×*c* | 1     | -2     | 1     | 0   |                 |                 |                  |
| Checking if *Δ* > 0               | 1     | -2     | 1     | 0   |                 |                 | no               |
| Checking if *Δ* = 0               | 1     | -2     | 1     | 0   |                 |                 | yes              |
| *x*<sub>1</sub> = –*b* / (2×*a*)  | 1     | -2     | 1     | 0   | 1               |                 |                  |
| *x*<sub>2</sub> does not exist    | 1     | -2     | 1     | 0   | 1               | none            |                  |
| **OUTPUT**                        | 1     | -2     | 1     | 0   | 1               | none            | **-4**, **none** |

Solving *x*<sup>2</sup> + 2 *x* + 3 = 0:

| STEP                                            | *a* | *b* | *c* | *Δ* | *x*<sub>1</sub> | *x*<sub>2</sub> | RESULT             |
| ----------------------------------------------- | --- | --- | --- | --- | --------------- | --------------- | ------------------ |
| **INPUT**                                       |**1**|**2**|**3**|     |                 |                 |                    |
| *Δ* = *b*<sup>2</sup> – 4×*a*×*c*               | 1   | 2   | 3   | 0   |                 |                 |                    |
| Checking if *Δ* > 0                             | 1   | 2   | 3   | 0   |                 |                 | no                 |
| Checking if *Δ* = 0                             | 1   | 2   | 3   | 0   |                 |                 | no                 |
| *x*<sub>1</sub> and *x*<sub>2</sub> don't exist | 1   | 2   | 3   | 0   | none            | none            |                    |
| **OUTPUT**                                      | 1   | 2   | 3   | 0   | none            | none            | **none**, **none** |

Let's consider another case: *a* = 0, *b* = 2, *c* = 3:

| STEP                                      | *a*   | *b*   | *c*   | *Δ* | *x*<sub>1</sub>            | *x*<sub>2</sub> | RESULT |
| ----------------------------------------- | ----- | ----- | ----- | --- | -------------------------- | --------------- | ------ |
| **INPUT**                                 | **0** | **2** | **3** |     |                            |                 |        |
| *Δ* = *b*<sup>2</sup> – 4×*a*×*c*         | 0     | 2     | 3     | 4   |                            |                 |        |
| Checking if *Δ* > 0                       | 0     | 2     | 3     | 4   |                            |                 | yes    |
| *x*<sub>1</sub> = (–*b* – √*Δ*) / (2×*a*) | 0     | 2     | 3     | 4   | <span style="color: red">0/0</span> |        |        |

Can you see what happened? Out algorithm failed for a case where *a* = 0! What can be done about it? Well, we need to explicitly check this case. So the algorithm will be:

```
INPUT:
  a, b, c — eqution coeffi      ients.

STEPS:
  — Check if a ≠ 0, if so:
    │ — Compute Δ = b² - 4×a×c
    │ — If Δ > 0 do the following:
    │   │ — Compute first solution x₁ = (-b - √Δ) / (2×a)
    │   │ — Compute second solution x₂ = (-b + √Δ) / (2×a)
    │   Else if Δ = 0:
    │   │ — Compute the only solution -b / (2×a) and name it ‘x₁’ for consistency
    │   │ — The second solution (x₂) does not exits
    │   If neither of the above is true (because Δ < 0), then:
    │   │ — Neither x₁ nor x₂ exist
    Else (regarding the condition a ≠ 0, so actually we handle case a = 0 below):
    │ — Compute the only solution to the linear equation x₁ = -c / b
    │ — x₂ obviously does not exist here (but we must remember to mention this)

OUTPUT:
  x₁, x₂
```

What you can see above is a **nested conditional**. First we check one condition (*a* ≠ 0) and in one of the cases we check another one (*Δ* > 0 or *Δ* = 0). When you write your own algorithms, clearly mark which block is nested in which!

Please trace this algorithm for the equations *x*<sup>2</sup> + 2 *x* – 8 = 0, *x*<sup>2</sup> – 2 *x* + 1 = 0, *x*<sup>2</sup> + 2 *x* + 3 = 0, and 2 *x* + 4 = 0 (*a* = 0) yourself.

## Summary

During the course, you will learn a formal programming language. This means that, that you will have to carefully comply to its semantic rules, where every single character matters. At the same time, you will have to write a precise algorithm realizing given task. Considering these two matters at once may be (in the beginning) too much for you. For this reason, I suggest first to write algorithms using your natural language, as shown above. You must always clearly identify the input, the output and precisely write all the necessary steps. Also remember to mark all the intermediate values and always use their names (don't use prepositions). Once you have done this, track your algorithm by hand, as shown above.

Having done this, you should have no problem to rewrite the algorithm using the formal programming language, rules of which you will learn in the coming weeks.

<hr/>

Published under [Creative Commons Attribution-NonCommercial-ShareAlike](https://creativecommons.org/licenses/by-nc-sa/4.0/) license.
