---
parent: "Classes and Objects: Basis"
grand_parent: Programming for Modelling and Data Analysis
nav_order:  3
---

# Custom data types

Looking at **objects** and **classes**, you might have noticed a similarity with **variables** and their **types**. In fact this is exactly the same. By defining a class, you create a new type and a class instance is simply a variable of this type. Built-in Python types are also classes. Notice that you have already used their methods:

```python
name = "python"
print(name.upper())  # `upper()` is a method in `str` class
```

You may define any type you want. Consider a class defining a fraction. It should have two attributes, *nominator* (named shortly `nom`) and *denominator* (`denom`):

```python
class Fraction:
    def __init__(self, nom, denom):
        self.nom = nom
        self.denom = denom
```

It is possible to perform mathematical operations on fractions, like addition, subtraction, multiplication and division. Let's define a function `mul` that takes two fractions, multiplies them, and returns a `Fraction` instance, which is their factor:

```python
def mul(a, b):
    return Fraction(a.nom * b.nom, a.denom * b.denom)
```

Actually this function is specific for fractions only. So, in order to keep things together, it is better to make it a method in a fraction:

```python
class Fraction:
    def __init__(self, nom, denom):
        self.nom = nom
        self.denom = denom

    def mul(self, other):
        return Fraction(self.nom * self.nom, self.denom * self.denom)
```

We may use this method as follows:

```python
x = Fraction(1, 2)
y = Fraction(5, 6)

z = x.mul(y)
```

The last line does not look good. Later in this course, you will learn what you can do to be able to use normal mathematical operators (`z = x * y`) for your classes.

<hr/>

Published under [Creative Commons Attribution-NonCommercial-ShareAlike](https://creativecommons.org/licenses/by-nc-sa/4.0/) license.
