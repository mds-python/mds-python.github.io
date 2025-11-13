---
parent: "Testing Your Code"
grand_parent: Programming for Modelling and Data Analysis
nav_order: 1
---

# Writing unit tests

## Why unit tests?

When writing code, it is important to ensure that it works as expected. One way to do this is by writing *unit tests*. Unit tests are small pieces of code that test individual units or components of your code to verify that they behave as intended.

Unit tests are important for several reasons:
1. **Catch Bugs Early**: By testing individual components, you can catch bugs early in the development process, making them easier and cheaper to fix.
2. **Facilitate Change**: Unit tests provide a safety net when making changes to your code. If you modify a component and the tests fail, you know immediately that something is wrong.
3. **Documentation**: Unit tests can serve as documentation for your code. They show how the code is intended to be used and what its expected behavior is.
4. **Improve Design**: Writing tests can help you think about your code's design and architecture, leading to better-structured and more maintainable code.

## `unittest` module

In Python, you can use the built-in `unittest` framework to write and run unit tests. Here's a simple example to illustrate how to create and run unit tests.

```python
import unittest

def is_even(x: int) -> bool:
    return x % 2 == 0

class TestIsEven(unittest.TestCase):
    def test_even_number_returns_true(self):
        self.assertTrue(is_even(4))

    def test_odd_number_returns_false(self):
        self.assertFalse(is_even(5))

if __name__ == "__main__":
    unittest.main()  # allows running this file directly
```

In this example, we define a simple function `is_even` that checks if a number is even. We then create a test case class `TestIsEven` that inherits from `unittest.TestCase`. Inside this class, we define two test methods: `test_even_number_returns_true` and `test_odd_number_returns_false`, which test the behavior of the `is_even` function.

To run the tests, you can execute the script directly, and the `unittest` framework will run all the test methods defined in the `TestIsEven` class.

## Organizing unit tests

Most tests written with the `unittest` framework are organized as classes that derive from `unittest.TestCase`.

- Group related tests into a `Test...` class. The class name should start with `Test` and describe what is being tested, for example `class TestMathUtils(unittest.TestCase):` or `class TestStringHelpers(unittest.TestCase):`.
- Put individual checks into methods whose names start with `test_`. The test runner discovers and runs any method beginning with `test_`.
- Keep each test method focused: one logical assertion or behavior per test method. This makes failures easier to interpret.
- Name test methods clearly to explain the expected behavior, for example `test_add_positive_numbers`, `test_raises_on_invalid_input`, `test_returns_empty_list_when_no_items`.
- Avoid putting multiple unrelated assertions in a single test method — if you must, prefer splitting into several test methods.
- Keep tests independent: they should not rely on global state left by other tests.

Example layout inside a package:

```
project/
    package/
        utils.py
        other.py
    tests/
        test_utils.py       # contains TestUtils (Test... classes and test_ methods)
        test_other.py
```

With this structure and clear naming, test discovery is reliable and the VS Code test explorer and other tools will show readable test names that map back to your code.


## Available assertions

The `unittest.TestCase` class provides several assertion methods to check for different conditions in your tests. Here are some commonly used assertions:

- `self.assertEqual(a, b)`: Check that `a` is equal to `b`.
- `self.assertNotEqual(a, b)`: Check that `a` is not equal to `b`.
- `self.assertTrue(x)`: Check that `x` is `True`.
- `self.assertFalse(x)`: Check that `x` is `False`.
- `self.assertIsNone(x)`: Check that `x` is `None`.
- `self.assertIsNotNone(x)`: Check that `x` is not `None`.
- `self.assertIn(a, b)`: Check that `a` is in `b`.
- `self.assertNotIn(a, b)`: Check that `a` is not in `b`.
- `self.assertRaises(exception, callable, *args, **kwargs)`: Check that calling `callable` with the given arguments raises the specified `exception`.

Below are short examples that show how the most common assertions are used in practice.

```python
class TestAssertions(unittest.TestCase):
    def test_equal_and_not_equal(self):
        self.assertEqual(2 + 2, 4)
        self.assertNotEqual(2 + 2, 5)

    def test_true_false(self):
        self.assertTrue(1 < 2)
        self.assertFalse(1 > 2)

    def test_is_none(self):
        x = None
        self.assertIsNone(x)

    def test_in_and_not_in(self):
        self.assertIn('py', 'python')
        self.assertNotIn('java', 'python')

    def test_combined_examples(self):
        items = [1, 2, 3]
        self.assertEqual(len(items), 3)
        self.assertTrue(isinstance(items, list))

```

### Using assertRaises

Testing that code raises the expected exception is common. `unittest` provides two ways to assert exceptions:

1. The context-manager form (preferred when you want to run a block of code and optionally inspect the exception object).
2. The callable form, where you pass the callable and its arguments to `assertRaises`.

Examples:

```python
class TestExceptions(unittest.TestCase):
    # Context manager form (recommended for readability)
    def test_divide_by_zero_context(self):
        with self.assertRaises(ZeroDivisionError) as cm:
            _ = 1 / 0
        # optional: inspect the exception
        self.assertIn('division', str(cm.exception))

    # Callable form
    def test_divide_by_zero_callable(self):

        def divide_by_zero():
            return 1 / 0

        self.assertRaises(ZeroDivisionError, divide_by_zero)

    # Another example: check that invalid index raises IndexError
    def test_index_error(self):
        lst = []
        with self.assertRaises(IndexError):
            _ = lst[0]

```

Notes and tips:
- Prefer the context-manager form when you need to run several lines and/or inspect the exception object.
- Use the callable form for short one-liners when that is clearer.
- Be explicit about the specific exception you expect — don't assert a broad Exception unless truly necessary.



<hr/>

Published under [Creative Commons Attribution-NonCommercial-ShareAlike](https://creativecommons.org/licenses/by-nc-sa/4.0/) license.
