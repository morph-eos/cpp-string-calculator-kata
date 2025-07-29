# Contributing Guide

Thank you for your interest in contributing to the String Calculator Kata C++ project!

## How to Contribute

### Bug Reports

If you find a bug, please:

1. Check if the bug hasn't already been reported in the Issues
2. Create a new Issue with:
   - Clear description of the problem
   - Steps to reproduce the bug
   - Expected vs actual output
   - Information about your environment (OS, compiler, etc.)

### Feature Proposals

To suggest new features:

1. Open a "Feature Request" type Issue
2. Clearly describe the proposed functionality
3. Explain why it would be useful
4. Provide usage examples

### Pull Requests

1. Fork the repository
2. Create a branch for your feature (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Code Standards

- Follow the existing code style
- Add tests for new features
- Ensure all tests pass
- Comment code when necessary
- Use descriptive variable and function names

### Testing

Before submitting a PR:

```bash
# Compile the project
g++ -std=c++11 -o calculator C-String-Calculator-Kata.cpp

# Run all tests
# (Specific instructions for your test environment)
```

## Local Development

### Setup

1. Clone the repository
2. Open with your preferred C++ IDE
3. Compile and test

### Project Structure

- `add.h` - Main calculator logic
- `C-String-Calculator-Kata.cpp` - User interface
- `Test-C-String-Calculator-Kata/` - Test suite

## Questions?

If you have questions, don't hesitate to open an Issue with the "question" label.
