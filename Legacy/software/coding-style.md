---
nav_order: 3
parent: Software
grand_parent: Legacy
has_children: false
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

Dependency injection is a technique used to ensure our code can be unit tested with mocks of all dependencies used by our code. It fundamentally relies on all our code receiving all of its dependencies externally rather than instantiating any dependencies internally.

### What is a Dependency?

Anything that can be described as a "uses a" relationship between classes. For example, all Mbed classes we use are dependencies of the classes we write, so Mbed’s `CAN` class is a dependency of our `CANInterface` class, because `CANInterface` "uses a" `CAN` object.

### How are Dependencies Mocked?

FakeIt is used to create an instance of a mock of our Mbed dependencies. Then that mock instance is passed to the unit of code (usually a class) we are testing. This tricks our code to think all Mbed dependencies are real Mbed implementations when they are actually all mocks with little or no actual functionality implemented.

### How this Affects how we Write our Code

All dependencies (specifically Mbed objects) we use in any of our libraries must be instantiated outside of our libraries and simply passed in on initialization. For classes we write, this means the constructor must take in all Mbed dependencies as inputs and store references or pointers to these inputs instead of simply initializing these dependencies in the constructor.

The actual initialization of all Mbed dependencies must be done either in main.cpp (for release builds) or in testing code via the mocking API (for testing). In either case, the initialized dependencies will be passed in to our initialization or constructors to fill the pointers/references.

This works because of polymorphism: the mock instances are effectively concrete subclasses of the abstract Mbed mock classes we write.

### Example

Below is the definition of our `CANInterface` class. 

```
class CANInterface
{
public:
    CANInterface(CAN &c, CANParser &cp, Thread &tx_thread, Thread &rx_thread, DigitalOut *stby=nullptr, std::chrono::milliseconds can_period = 1s);
    void startCANTransmission(void);

private:
    void rx_handler(void);
    void tx_handler(void);

    CAN &can;
    CANParser &can_parser;
    DigitalOut *standby;

    Thread &tx_thread;
    Thread &rx_thread;

    std::chrono::milliseconds tx_period;
};
```

Notice how the constructor accepts all Mbed dependencies used by the `CANInterface` class as reference or pointer inputs. For example the `CAN` object is taken as a reference, while the `DigitalOut` object is taken as a pointer. The distinction between whether a dependency should be a reference and a pointer is that optional dependencies should be pointers (which can be null), while required dependencies should be references (which cannot be null). So in our example, the `DigitalOut` object is optional, while all other Mbed dependencies are required.

Note that when using references for class data fields, they must be instantiated *before* the start of the constructor. This can be done as shown in the implementation of our `CANInterface` class constructor, using [C++ constructor initialization lists](https://en.cppreference.com/w/cpp/language/constructor). 

```
CANInterface::CANInterface(CAN &c, CANParser &cp, Thread &tx_thrd, Thread &rx_thrd, DigitalOut *stby, std::chrono::milliseconds tx_prd) : can(c), can_parser(cp), tx_thread(rx_thrd), rx_thread(tx_thrd), tx_period(tx_prd)
{
    if(stby) 
    { 
        standby = stby;
        *standby = 0;   // active low
    }
}
```

## Coding Standard

TODO
