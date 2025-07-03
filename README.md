# BigReal Number Library

A C++ library for handling arbitrary precision real numbers with custom comparison and arithmetic operations.

## Features

- **Arbitrary Precision**: Handle very large or very small real numbers beyond standard data type limits
- **Custom Operators**: Overloaded operators for comparison and arithmetic operations
- **Sign Handling**: Proper handling of positive and negative numbers in all operations

## Operators

### Comparison Operators

#### Greater Than (`>`)
Compares two BigReal numbers:
- If first number is positive and second is negative → first is greater
- If same sign:
  - Compare integer parts digit by digit from left to right
  - For decimals, smaller absolute value is considered greater
  - If integer parts equal, compare fractional parts from left to right

#### Less Than (`<`)
Compares two BigReal numbers:
- If left is negative and right is positive → left is smaller
- If same sign:
  - Compare integer parts digit by digit from right to left
  - For negative numbers, smaller absolute value is greater
  - If integers equal, compare fractions from left to right

### Arithmetic Operators

#### Addition (`+`)
Adds two BigReal numbers:
- **Same signs**: Add values normally, preserve sign
- **Different signs**: Perform subtraction
- **Process**: 
  1. Add fractional parts from right to left
  2. Handle carry from fraction to integer part
  3. Add integer parts with carry
  4. Result sign matches the larger absolute value

#### Subtraction (`-`)
Subtracts two BigReal numbers using addition:
- Converts `A - B` to `A + (-B)`
- Handles all sign combinations:
  - `(-A) - (-B)` = `-A + B`
  - `(-A) - (+B)` = `-A - B`
  - `(+A) - (-B)` = `A + B`


## Implementation Details

- Numbers stored as strings for precision
- Separate handling of integer and fractional parts
- Carry propagation in arithmetic operations
- Sign management for all operations

