# Practical Examples - String Calculator

This guide provides practical examples of using the String Calculator with various inputs and their expected results.

## Basic Examples

### Empty String

```cpp
Input:  ""
Output: 0
```

### One Number

```cpp
Input:  "1"
Output: 1

Input:  "42"  
Output: 42
```

### Two Numbers

```cpp
Input:  "1,2"
Output: 3

Input:  "10,15"
Output: 25
```

## Advanced Examples

### Multiple Numbers

```cpp
Input:  "1,2,3,4,5"
Output: 15

Input:  "10,20,30,40,50"
Output: 150
```

### Newlines as Separators

```cpp
Input:  "1\n2,3"
Output: 6
Explanation: 1 + 2 + 3 = 6

Input:  "4\n5\n6"
Output: 15
Explanation: 4 + 5 + 6 = 15
```

### Custom Delimiters

```cpp
Input:  "//;\n1;2"
Output: 3
Explanation: Delimiter ';', so 1 + 2 = 3

Input:  "//|\n1|2|3"
Output: 6
Explanation: Delimiter '|', so 1 + 2 + 3 = 6

Input:  "//*\n2*3*4"
Output: 9
Explanation: Delimiter '*', so 2 + 3 + 4 = 9
```

### Large Numbers (> 1000)

```cpp
Input:  "2,1001"
Output: 2
Explanation: 1001 is ignored, so only 2

Input:  "1000,1001,2"
Output: 1002
Explanation: 1001 is ignored, so 1000 + 2 = 1002

Input:  "5,2000,10,3000"
Output: 15
Explanation: 2000 and 3000 are ignored, so 5 + 10 = 15
```

## Error Handling

### Negative Numbers

```cpp
Input:  "1,4,-1"
Output: Exception: "negatives not allowed: -1"

Input:  "-1,-2,3"
Output: Exception: "negatives not allowed: -1" (first negative found)

Input:  "1,-4,5,-8"
Output: Exception: "negatives not allowed: -4" (first negative found)
```

### Invalid Inputs (handled by application)

```cpp
Input:  "1,\n"    // Invalid but doesn't throw exception in add() function
Input:  "1,,2"    // Will generate conversion error
Input:  "abc,2"   // Will generate conversion error
```

## Complex Examples

### Multiple Combinations

```cpp
Input:  "//;\n1;2;1001;3"
Output: 6
Explanation: Delimiter ';', 1001 ignored, so 1 + 2 + 3 = 6

Input:  "1\n2,3,1500,4"
Output: 10
Explanation: 1500 ignored, so 1 + 2 + 3 + 4 = 10
```

## Interactive Testing

You can test these examples using:

1. **Manual Input**: Run the program and select option 1
2. **File Input**: Modify `input.txt` with one of the examples above and select option 2

### Example Session

``` sh
Choose an option:
1. Enter the string manually
2. Load the string from the input.txt file
1
Enter the string: 1,2,3,4,5
Result: 15
```

## Implementation Notes

- The `add()` function in `add.h` handles all the logic
- Tests in `Test-C-String-Calculator-Kata.cpp` cover all these scenarios
- The main application provides a user-friendly interface to test the function
