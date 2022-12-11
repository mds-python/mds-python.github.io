---
parent: "Classes and Objects: Intermediate"
grand_parent: Programming for Modelling and Data Analysis
nav_order:  1
---

# Special methods

## Arithmetical operations

Let's go back to our [`Fraction` class](../09%20Classes%20and%20Objects%20Basis/3%20Custom%20data%20types):

```python
class Fraction:
    def __init__(self, nom, denom):
        self.nom = nom
        self.denom = denom

    def mul(self, other):
        return Fraction(self.nom * self.nom, self.denom * self.denom)
```

Such formulation allows us to multiply two fractions in an ugly way `c = a.mul(b)`. It would be much more clear if we were able to write `c = a * b`. In fact we can. Let's rename the method `mul` to `__mul__` (two underscored in the beginning and the end, like in `__init__`):

```python
class Fraction:
    def __init__(self, nom, denom):
        self.nom = nom
        self.denom = denom

    def __mul__(self, other):
        return Fraction(self.nom * self.nom, self.denom * self.denom)
```

Now we can write:

```python
x = Fraction(1, 2)
y = Fraction(5, 6)

z = x * y
```

Methods with two underscores in the beginning and the end are [*special methods*](https://diveintopython3.net/special-method-names.html). Generally you never invoke them directly. For example, you never call the `__init__` method explicitly. It is automatically invoked on instance creation. `__mul__` is another such method and it is called when two objects are multiplied.

There are many such methods. You can find the list of all of them in the [documentation](https://docs.python.org/3/reference/datamodel.html#special-method-names). Here are the most basic ones used for arithmetics:

| You want…          | So you write… | And the special function is… |
| ------------------ | ------------- | ---------------------------- |
| addition           | `x + y`       | `x.__add__(y)`               |
| subtraction        | `x - y`       | `x.__sub__(y)`               |
| multiplication     | `x * y`       | `x.__mul__(y)`               |
| division           | `x / y`       | `x.__truediv__(y)`           |
| modulo (remainder) | `x % y`       | `x.__mod__(y)`               |
| raise to power     | `x ** y`      | `x.__pow__(y)`               |

Please implement `__add__`, `__sub__` and `__truediv__` for the `Fraction` class.


## Pretty-printing objects

Other special methods allow to access “elements” of our class using square brackets (like for lists or dictionaries) ([`__getitem__`](https://docs.python.org/3/reference/datamodel.html#object.__getitem__) and [`__setitem__`](https://docs.python.org/3/reference/datamodel.html#object.__setitem__)), getting the “length” of our custom sequence ([`__len__`](https://docs.python.org/3/reference/datamodel.html#object.__len__)), etc.

An important special method you should always implement is `__str__`. Consider the following code:

```python
class Fraction:
    def __init__(self, nom, denom):
        self.nom = nom
        self.denom = denom

frac = Fraction(1, 2)

print(frac)
```

If you run it, the output will be something like:

```
<__main__.Fraction object at 0x7f61ad175b80>
```

This is not very useful. Luckily, the `__str__` method can be used to convert the class into a string that can be printed:

```python
class Fraction:
    def __init__(self, nom, denom):
        self.nom = nom
        self.denom = denom

    def __str__(self):
        # This method must RETURN a string. Do not try to print anything!
        return f"{self.nom}/{self.denom}"

frac = Fraction(1, 2)

print("Our fraction is:", frac)
```

This time the output looks much better:

```
Our fraction is: 1/2
```

## Object comparison

Some other special functions that are very useful are comparisons. Fractions can be equal (if both nominators and denominators equal) or one can be larger than another one. Special functions doing comparisons should always return `True` or `False`. Their names are as follow:

| Comparison | Special function    |
| ---------- | ------------------- |
| `x < y`    | `x.__lt__(self, y)` |
| `x <= y`   | `x.__le__(self, y)` |
| `x == y`   | `x.__eq__(self, y)` |
| `x != y`   | `x.__ne__(self, y)` |
| `x > y`    | `x.__gt__(self, y)` |
| `x >= y`   | `x.__ge__(self, y)` |



> **Note: Fraction reduction**
>
> When you implement arithmetic operation on fractions, you may end up with a reducible fraction, e.g. 2/3 × 3/5 = 6/15. Naturally, this fraction is equal to 2/5.
>
> In order to have your class behave elegantly and for comparisons to work, you should always reduce the fraction by dividing both the nominator and denominator by their [greatest common divisor](https://en.wikipedia.org/wiki/Greatest_common_divisor), which can be found using the function `gcd` in the `math` module. In which method you should do it? If you do this in every special method responsible for mathematical operation, you will need to do it several times. Furthermore, if someone creates an instance of you class e.g. as `Fraction(4, 6)`, the fraction will not be reduced. However if you make the reduction in the constructor, this will cover all use cases:
>
> ```python
> from math import gcd
>
> class Fraction:
>     def __init__(self, nom, denom):
>         r = gcd(nom, denom)
>         self.nom = nom // r      # we use // for integer division
>         self.denom = denom // r
>
>     def __str__(self):
>         return f"{self.nom}/{self.denom}"
>
>     def __mul__(self, other):
>         return Fraction(self.nom * self.nom, self.denom * self.denom)
> ```
>
> Also in the constructor you can do more sanitizations, like checking if the denominator is not 0 (and raising `ValueError` in such case), making sure that the denominator is always positive (and the sign of the nominator is adjusted accordingly), etc.

<hr/>

Published under [Creative Commons Attribution-NonCommercial-ShareAlike](https://creativecommons.org/licenses/by-nc-sa/4.0/) license.
