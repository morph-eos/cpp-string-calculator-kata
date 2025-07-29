# String Calculator Kata - C++ Version

[![License: GPL v2](https://img.shields.io/badge/License-GPL%20v2-blue.svg)](https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html)
[![C++](https://img.shields.io/badge/C%2B%2B-11%2B-blue.svg)](https://isocpp.org/)
[![TDD](https://img.shields.io/badge/Development-TDD-red.svg)](https://en.wikipedia.org/wiki/Test-driven_development)
[![Kata](https://img.shields.io/badge/Type-Coding%20Kata-orange.svg)](http://osherove.com/tdd-kata-1)

A complete implementation of the famous String Calculator Kata in C++, developed following Test-Driven Development (TDD) principles.

## Table of Contents

- [Overview](#overview)
- [Quick Start](#quick-start)
- [Implemented Features](#implemented-features)
- [Project Structure](#project-structure)
- [How to Use](#how-to-use)
- [Execution Instructions](#execution-instructions)
- [Kata Specification](#kata-specification)
- [Test Coverage](#test-coverage)
- [Troubleshooting](#troubleshooting)
- [FAQ](#faq)
- [Additional Files](#additional-files)
- [Credits](#credits)

## Overview

This project implements all steps of the String Calculator Kata, a classic programming exercise that emphasizes test-driven development, incremental refactoring, and clean code writing.

## Quick Start

```bash
# Clone the repository
git clone https://github.com/morph-eos/cpp-string-calculator-kata.git
cd cpp-string-calculator-kata

# Compile and run
g++ -std=c++11 -o calculator C-String-Calculator-Kata.cpp
./calculator

# Select option 1 and try: 1,2,3,4,5
```

## Implemented Features

✅ **Step 1**: Basic calculator for 0, 1 or 2 numbers  
✅ **Step 2**: Handle unknown amount of numbers  
✅ **Step 3**: Support for newlines as separators  
✅ **Step 4**: Custom delimiters  
✅ **Step 5**: Negative numbers handling with exceptions  
✅ **Step 6**: Ignore numbers greater than 1000  

## Project Structure

``` sh
cpp-string-calculator-kata/
├── add.h                           # Main implementation of add() function
├── C-String-Calculator-Kata.cpp    # Main application with user interface
├── input.txt                       # Input file for manual testing
├── Test-C-String-Calculator-Kata/  # Complete test suite
│   ├── Test-C-String-Calculator-Kata.cpp
│   └── pch.h
├── *.vcxproj                       # Visual Studio project files
└── README.md                       # This documentation
```

## How to Use

### Mode 1: Manual Input

1. Run the program
2. Select option `1`
3. Enter the number string to calculate

### Mode 2: File Input

1. Modify the `input.txt` file with your string
2. Run the program
3. Select option `2`

### Valid Input Examples

```cpp
""          // Result: 0
"1"         // Result: 1
"1,2"       // Result: 3
"1,2,3,4,5" // Result: 15
"1\n2,3"    // Result: 6 (newline + comma)
"//;\n1;2"  // Result: 3 (custom delimiter)
"2,1001"    // Result: 2 (1001 ignored)
```

**Note:** When testing custom delimiters manually, the format `//;\n1;2` should be entered as a single line. For multiline inputs, use the file input mode.

## Execution Instructions

### Prerequisites

- C++ compiler compatible with C++11 or higher
- C++ IDE (Visual Studio, Visual Studio Code, Code::Blocks, etc.)
- Microsoft Unit Testing Framework (for running tests)

### Compilation and Execution

#### With Visual Studio

1. Open the `C-String-Calculator-Kata.sln` file
2. Build the project (Build → Build Solution)
3. Run the application (Debug → Start Without Debugging)

#### With GCC/Clang

```bash
# Compilation (GCC)
g++ -std=c++11 -o calculator C-String-Calculator-Kata.cpp

# Compilation (Clang on macOS)
clang++ -std=c++11 -o calculator C-String-Calculator-Kata.cpp

# Execution
./calculator
```

#### Running Tests

**With Visual Studio:**

1. Open the test project in Visual Studio
2. Go to Test → Run All Tests
3. Verify that all tests pass

**Manual Testing (without Visual Studio):**

1. Compile and run the main application
2. Test various input scenarios from the examples section
3. Verify outputs match expected results

**Example Test Scenarios:**

```bash
# Test basic functionality
echo -e "1\n1,2,3" | ./calculator

# Test negative numbers (should show error)
echo -e "1\n1,-2,3" | ./calculator

# Test large numbers (should ignore >1000)
echo -e "1\n2,1001,3" | ./calculator
```

## Kata Specification

### Step 1: The simplest thing

Create a simple String calculator with a method `int add(String numbers)`.

- The string argument can contain 0, 1 or 2 numbers and will return their sum
- For an empty string it will return 0
- Examples: `""`, `"1"`, `"1,2"`

### Step 2: Handle an unknown amount of numbers

Allow the `add()` method to handle an unknown amount of numbers.

### Step 3: Handle new lines between numbers

Allow the `add()` method to handle new lines between numbers (instead of commas).

- This input is valid: `"1\n2,3"` (result: 6)
- This input is NOT valid: `"1,\n"`

### Step 4: Support different delimiters

Support different delimiters: to change a delimiter, the beginning of the string will contain a separate line that looks like this:

`"//[delimiter]\n[numbers...]"`

For example `"//;\n1;2"` should return 3 where the default delimiter is `';'`.

The first line is optional. All existing scenarios should still be supported.

### Step 5: Negative numbers

Calling `add()` with a negative number will throw an exception `"negatives not allowed"` - and the negative that was passed.

For example `add("1,4,-1")` should throw an exception with the message `"negatives not allowed: -1"`.

If there are multiple negatives, show all of them in the exception message.

### Step 6: Ignore big numbers

Numbers bigger than 1000 should be ignored, so adding 2 + 1001 = 2

## Test Coverage

The project includes a comprehensive test suite that covers:

- ✅ Empty string
- ✅ Single number
- ✅ Two numbers
- ✅ Unlimited number of numbers
- ✅ Newlines as separators
- ✅ Custom delimiters
- ✅ Negative numbers handling
- ✅ Ignore numbers > 1000

## Troubleshooting

### Common Compilation Issues

**Missing headers:** If you get compilation errors about missing headers, ensure you have:

- `<string>` for string operations
- `<sstream>` for string stream parsing
- `<stdexcept>` for exception handling
- `<iostream>` and `<fstream>` for I/O operations

**C++11 Standard:** Make sure to use the `-std=c++11` flag when compiling.

### Runtime Issues

**File not found:** If you get "Error opening the input.txt file", make sure the file exists in the same directory as the executable.

**Invalid conversion:** If you get conversion errors, check that your input contains only valid numbers and delimiters.

## FAQ

### Q: What happens if I enter non-numeric characters?

A: The program will throw a `std::invalid_argument` exception during conversion.

### Q: Can I use multiple delimiters in the same string?

A: No, the format supports only one custom delimiter per string. However, you can combine the custom delimiter with newlines.

### Q: Why are numbers > 1000 ignored?

A: It's part of the kata specification to demonstrate handling of specific business rules.

### Q: How can I add new tests?

A: Modify the `Test-C-String-Calculator-Kata.cpp` file and add new `TEST_METHOD` methods.

### Q: Does the program support decimal numbers?

A: No, it currently supports only integers.

## Additional Files

- **[EXAMPLES.md](EXAMPLES.md)** - Detailed practical examples
- **[CONTRIBUTING.md](CONTRIBUTING.md)** - Guide for contributing to the project

## Credits

Original kata created by [Roy Osherove](http://osherove.com/tdd-kata-1).
