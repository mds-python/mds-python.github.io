# Complex numbers

Python has a type representing complex numbers natively (`complex`). It can be created by adding a symbol `j` to the real numbers to denote the imaginary part. For example:

```python
complex_value = 1 + 0.2j
```

On this type, you can perform normal calculations, print it, etc. But what if we want to extract only the real or imaginary part from a complex number? For this purpose, we use the *attributes* `real` and `imag`. Attributes are similar to methods: they are used by entering their names after the dot like `variable.attribute`, but without the parentheses . E.g:

```python
complex_value = 1 + 0.2j 

print ("Re =", complex_value.real) 
print ("Im =", complex_value.imag)
```

<hr/>

Published under [Creative Commons Attribution-NonCommercial-ShareAlike](https://creativecommons.org/licenses/by-nc-sa/4.0/) license.
