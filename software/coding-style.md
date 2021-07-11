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
- YAGNI (You Aren't Gonna Need It)
    - Only implement what you need now

## Import Rules

- Angle brackets `<>` for external libraries (C/C++ standard libraries, Mbed, Unity, FakeIt)
    - e.g. `#include <mbed.h>` 
- Double quotes `""` for user/project libraries and headers (files we write)
    - e.g. `#include "CANInterface.h"`

## Variable Types

- Numeric Types
    - Avoid using 64-bit types, as this will put unnecessary strain on our MCU
        - This includes `double`, `int64_t`, and `uint64_t`
    - Avoid sending floating-point types over CAN
    - For integers, don't use the ambiguous types `int`, `unsigned int`, `short`, `long`, or `long long`
        - Instead use `int8_t`, `uint8_t`, `int16_t`, `int32_t`
    - Literals
        - For floating-point numbers, use the `f` suffix
            - e.g. `float x = 1.5f;`
            - Leaving out the `f` suffix will automatically use a double, putting unnecessary strain on the MCU
        - For integer numbers, use `L` for `int32_t`, `u` for `uint16_t` and `uint8_t`, `uL` for `uint32_t`, and no suffix for `int16_t` and `int8_t`
            - e.g. `uint16_t x = 123u;`
- Null Type
    - For pointers, use `nullptr`
        - This is the C++ equivalent of the `NULL` macro in C, but comes with explicit type checking
    - For `char` types, use `'\0'`
    - Never use the literal `0` for null pointers
- Time Durations
    - Use `std::chrono` durations for all time durations (as Mbed has deprecated the use of integer or float types for all time durations)
    - e.g. `std::chrono::milliseconds`
- References vs Pointers
    - Whenever possible, use references
    - Otherwise, use pointers
    - Reasons why you would need to use pointers include:
        - The variable may be null
        - The memory location of the variable may need to change (i.e. the pointer changes)
        - The initial memory location of the variable is unknown during initialization

## Formatting

- Use four spaces for indentation instead of the tab character `'\t'` (this can be changed via a setting in your IDE or text editor)

## Dependency Injection

TODO

## Coding Standard

TODO
