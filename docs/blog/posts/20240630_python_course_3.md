---
date: 2024-06-30
draft: True
authors: [gabrielbdornas]
comments: true
categories:
  - Python
  - Python course
---

# Python course - Class 3

Have you ever wanted to unlock the power of Python?
This versatile language is used by data scientists, web developers, and even hobbyists to automate tasks, analyze information, and build incredible applications.

<!-- more -->

This content is designed to take you from absolute beginner to Python pro, guiding you step-by-step through the fundamentals and helping you put your newfound skills to the test with exciting projects.
Get ready to join the thriving Python community, let's get started!


## Arithmetic operations

- They are the same arithmetic operations we have in math:

    ```python
    # addiction
    print(30 + 4) # (1)!

    # subtraction
    print(30 + 4) # (2)!

    # multiplication
    print(30 * 4) # (3)!

    # float division
    print(30 / 4) # (4)!

    # integer division
    print(30 // 4) # (5)!

    # modulis
    print(30 % 4) # (6)!

    # power
    print(30 ** 4) # (7)!
    ```

    1. :man_raising_hand: Try to use the formatted string options like `print(f'{30 + 4 = }')`.
    2. :man_raising_hand: Try to use the formatted string options like `print(f'{30 - 4 = }')`.
    3. :man_raising_hand: Try to use the formatted string options like `print(f'{30 * 4 = }')`.
    4. :man_raising_hand: Try to use the formatted string options like `print(f'{30 / 4 = }')`.
    5. :man_raising_hand: Try to use the formatted string options like `print(f'{30 // 4 = }')`.
    6. :man_raising_hand: Try to use the formatted string options like `print(f'{30 %% 4 = }')`.
    7. :man_raising_hand: Try to use the formatted string options like `print(f'{30 ** 4 = }')`.

## Augmented assignment operator:

```python
# addiction
add = 30
add += 4 # (1)!

# subtraction
sub = 30
sub -= 4 # (2)!

# multiplication
mult = 30
mult *= 4 # (3)!

# float division
float_div = 30
float_div /= 4 # (4)!

# integer division
int_div = 30
int_div //= 4 # (5)!

# modulis
mod = 30
mod %= 4 # (6)!

# power
pow = 30
pow **= 4 # (7)!
```

1. :man_raising_hand: `add` will be equal to `34`.
2. :man_raising_hand: `sub` will be equal to `26`.
3. :man_raising_hand: `mult` will be equal to `120`.
4. :man_raising_hand: `float_div` will be equal to `7.5`.
5. :man_raising_hand: `int_div` will be equal to `7`.
6. :man_raising_hand: `mod` will be equal to `2`..
7. :man_raising_hand: `pow` will be equal to `810000`.

## Operator precedence - PEMDAS

??? question "What will be the value of `x` in `x = 10 + 3 * 2`?"

    If you said `26` you must understand operator's precedence. **PEMDAS** stands for Parentheses, Exponents, Multiplication and Division, and Addition and Subtraction. This acronym serves as a useful mnemonic to remember the order of operations in Python. Which means that in `x = 10 + 3 * 2`, the `3 * 2` operation will be performed first, and its result will be add to `10`, totaling a final result equal to `16`. On the other hand, in `y = (10 + 3) * 2`, `y` will be equal to `26` because of the inclusion of the parentheses.

| Order | Rule Component              | Operators |
|-------|-----------------------------|-----------|
| 1st   | Parentheses                 | ()        |
| 2nd   | Exponents                   | **        |
| 3rd   | Multiplication and Division | *, /      |
| 4th   | Addition and Subtraction    | +, -      |

??? question "Your turn!"

    What's the result of the expressions?

    ```python
    x = (2 + 3) * 10 -3 # (1)!

    y = 10 + 3 * 2 ** 2 # (2)!

    z = 10 + 3 * (2 ** 2) # (3)!
    ```

    1. :man_raising_hand: The result will be `47`.
    2. :man_raising_hand: The result will be `22`.
    3. :man_raising_hand: The result will be `22`.

## Math functions

- Built-in math functions

    ```python
    round(2.9)

    abs(-2.9)

    min(5, 10, 25)

    max(5, 10, 25)

    pow(4, 3)
    ```

- The math module:

    ```python
    import math

    math.ceil(2.9)

    math.floor(2.9)

    math.pi
    ```

    # add python official documentation
    # add pprint as help
