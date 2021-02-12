# Keyboard input

Until now, the values ​​of variables were defined in the program code:

```python
variable1 = 1 
variable2 = 2
```

In real programs, data is usually downloaded from external sources - they can be data entered directly by the user (in a text console, graphical window, through a form on a website, etc.), but they can also be read from a file, sent from an external device ( e.g. measuring equipment), downloaded from the Internet, given as an argument of calling a program launched from the [command line](https://en.wikipedia.org/wiki/Command-line_interface).

A well-written program should be independent of the input method. We will discuss exactly how to achieve this later. Below, we will discuss how to read the data entered by the user directly from the keyboard, but from the very beginning it should be noted that **this stage should be separated from the calculation part, as well as writing the result on the screen using a function `print`**.

The function used to enter data from the keyboard is called `input`. It is used as follows:

```python
entered_value = input ("Question:")
```

The argument of this function (the text in parentheses) is the question that will be displayed to the user. When it is printed, the program will stop and wait for any string to be entered by the user (the string should be terminated by pressing the Enter key). Then, the entered value will be *returned* by the function `input`, i.e. placed somewhere in the memory and made available e.g. for assignment to a variable, for further use (in the above example, the variable named `entered_value` will point to the string entered by the user).

Note that in Python 3, the function input always returns a text string, which is a variable of type `str`. If we need a numeric value, it should be converted to the correct type, as described earlier:

```python
distance = float(input("Enter distance between points [m]:"))
```

In this example, the user will be prompted for a distance, and then the entered value will be immediately passed to the "function" `float` to be converted to a real number. The important point here is that at this moment we have no control over whether users enter the correct value that can be converted to a real number. If this is not the case, the program will be terminated with an error message (please check). A method to deal with this problem will be described later in the course.

As I wrote earlier, it is a good habit to separate the input and display part from the computational part. Thanks to this, in the future it will be much easier to change our program, e.g. in such a way that it reads data from one file and writes the results to another (this will be discussed later). So a poorly written program is:

```python
inches = 2.54 * float(input("Enter length in centimeters:")) 
print("Length in inches is:", inches)
```

This looks much better:

```python
# Input 
centimeters = float(input("Enter length in centimeters:")) 

# Calculation part 
inches = 2.54 * centimeters 

# Presentation of the result 
print("Length in inches is:", inches)
```

Please pay attention to write programs this way, **from the very beginning**!


<hr />

Published under [Creative Commons Attribution-NonCommercial-ShareAlike](https://creativecommons.org/licenses/by-nc-sa/4.0/) license.
