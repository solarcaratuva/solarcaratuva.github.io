---
nav_order: 3
parent: Software
---

# Coding Style

## Naming Conventions

- Class names should use `PascalCase`
    - File names for classes should use the exact same name as the class itself, e.g. `PascalCase.h` and `PascalCase.cpp`
- Function and variable names should use `snake_case`

## Software Development Principles

- DRY (Don't repeat yourself)
    - Minimize the amount of repeated code
- Rule of Three 
    - Refactor once code is repeated 3 or more times
- KISS (Keep it simple, stupid)
    - Limit the amount of code in each function (40-50 lines max)
- YAGNI (You Aren’t Gonna Need It)
    - Only implement what you need now

## Import Rules

- Angle brackets `<>` for external libraries (C/C++ standard libraries, Mbed, Unity, FakeIt)
    - e.g. `#include <mbed.h>` 
- Double quotes `“”` for user/project libraries and headers (files we write)
    - e.g. `#include "CANInterface.h"`

## Variable Types

## Formatting

## Dependency Injection


