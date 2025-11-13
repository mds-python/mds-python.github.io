---
parent: "Testing Your Code"
grand_parent: Programming for Modelling and Data Analysis
nav_order: 2
---

# Running unit tests

## Running unit tests from the command line

To run unit tests, you can use the command line. If you have a file named `test_is_even.py` containing the example tests, you can run the tests using the following command:

```bash
python -m unittest test_is_even.py
```

This will execute all the test methods in the `TestIsEven` class and report the results.

## Configuring tests in Visual Studio Code

Visual Studio Code has built-in test discovery and a test runner that integrates with Python's `unittest`, `pytest` and `nose` frameworks. The steps below show how to configure VS Code to discover and run `unittest` tests (the built-in framework) and a recommended file naming scheme.

1. Open the Command Palette (Ctrl+Shift+P / Cmd+Shift+P) and choose "Python: Configure Tests".
2. Select the test framework you want to use (choose "unittest").
3. Choose the folder to use as the test root (usually the workspace root).

VS Code will then add the necessary settings to your workspace. You can also add or edit those settings manually in `.vscode/settings.json`. Example settings that make test discovery consistent:

```json
{
  "python.testing.unittestEnabled": true,
  "python.testing.pytestEnabled": false,
  "python.testing.nosetestsEnabled": false,
  "python.testing.unittestArgs": [
    "-v",
    "-s",
    "",
    "-p",
    "test*.py"
  ]
}
```

Notes about the example:
- The `-s` argument controls the start directory for discovery; leaving it as an empty string uses the workspace root. If you put a relative path there (for example `tests`), discovery starts from that folder.
- The pattern `test*.py` tells the test discovery to look for files starting with `test` and ending with `.py`.

### Recommended file naming and layout

To make discovery reliable and keep tests organized, follow a simple naming scheme and layout:

- Place tests either alongside the code under test (same package) or in a top-level `tests/` folder.
- Name test files using one of these patterns:
  - `test_<module>.py` (e.g. `test_utils.py`) — common and recommended
  - `<module>_test.py` — also supported by many tools
- Name test classes using the `Test...` prefix (for `unittest.TestCase` subclasses), for example `class TestMathUtils(unittest.TestCase):`.
- Name individual test methods starting with `test_` so the test runner recognises them, e.g. `def test_add_positive_numbers(self):`.

Example layout (recommended):

- project/
  - package/
    - utils.py
    - other.py
  - tests/
    - test_utils.py
    - test_other.py

With this layout and the `.vscode/settings.json` discovery pattern above, VS Code will discover the tests and show them in the Testing sidebar. You can run or debug single tests from the editor or the sidebar.

### Running and debugging in VS Code

- Use the Testing view (the beaker icon) to run or debug tests interactively.
- Hover over a discovered test in the editor to see Run and Debug codelenses.
- Use the output panel and Test Log to inspect failures and stack traces.


<hr/>

Published under [Creative Commons Attribution-NonCommercial-ShareAlike](https://creativecommons.org/licenses/by-nc-sa/4.0/) license.
