---
parent: Algorithms and Programs
grand_parent: Programming for Modelling and Data Analysis
nav_order:  E
---

# Algorithmic thinking exercises

   Below you have a set of problems. In each one identify and name the necessary input, write precisely all the necessary steps (as in the examples shown earlier), and identify the algorithm result (the output).

1. Given a temperature expressed in degrees Celsius, convert it into its Fahrenheit equivalent.

   Conversion formula: *°F* = 9/5 × *°C* + 32

2. A bank allows conversion of some euro deposit into Polish złoty. The current conversion rate is 1 EUR = 4.60 PLN.
   For each transaction, the bank takes 2% commission. Hence, for example, exchanging 100 EUR will give 450.80 PLN. Show the conversion algorithm.

3. Family Allowance is a cash amount, paid monthly, to help families in supporting and educating children.
   To receive this allowance, the family must have a reference income equal to or less than the established value € 8803.62.
   It is known that the reference income is calculated using the following formula:

    *reference income* = *total household income* / (*number of children* + 1)

    Determine if a given family (with a given total household income and a given number of children) is eligible for the allowance (the answer should be `True` or `False`).

4. Build an algorithm that calculates a person's Body Mass Index and physical condition. The formula is
   *BMI* = *weight* / *height*², where *weight* is given in **kilograms** and *height* in **meters**.

   The person's condition can be read from the following table:

   | Condition             | BMI Women   | BMI Men     |
   | --------------------- | ----------- | ----------- |
   | Underweight           | < 19.1      | < 20.7      |
   | Normal weight         | 19.1 - 25.8 | 20.7 – 26.4 |
   | Marginally overweight | 25.8 - 27.3 | 26.4 – 27.8 |
   | Above ideal weight    | 27.3 - 32.3 | 27.8 – 31.1 |
   | Obese                 | > 32.3      | > 31.1      |

   Determine the person's condition given the weight, height in centimeters and the gender.

5. The metabolism rate is calculated using the following formula:

   *metabolism rate* = 655 + 9.6 × *body weight in kg* + 1.8 × *height in centimeters* + 4.7 × *age*.

   To calculate the number of kilo-calories a person must eat daily, you should determine his/her metabolism rate and multiply it by a correction factor, which depends on the style of living:

   | Correction factor | Exercise type                                       |
   | ----------------- | --------------------------------------------------- |
   | 1.200             | Sedentary                                           |
   | 1.375             | Does light exercise (1 to 3 times a week)           |
   | 1.550             | Practices moderate exercise (4 or 5 times a week)   |
   | 1.725             | Has a high degree of activity (6 or 7 times a week) |

   Determine the number of calories one should eat basing on the number of exercises per week all other necessary information.

6. In some European country, the Automobile Tax depends on a car's engine capacity. It is computed as:

   *tax* = *engine capacity in cm³* × *tax rate* – *discount*

   where the *rate* and *discount* are given in the table below:

   | Tax rate [EUR] | Cylinder capacity [cm³] | Discount [EUR] |
   | -------------- | ----------------------- | -------------- |
   | 3.74           | up to 1250              | 2417.56        |
   | 8.86           | more than 1250          | 8813.22        |

   Write an algorithm that computes the automobile tax. Remember that the tax cannot be less than 0 (this is an unlikely case, but you must consider it anyway).


<hr/>

Published under [Creative Commons Attribution-NonCommercial-ShareAlike](https://creativecommons.org/licenses/by-nc-sa/4.0/) license.
