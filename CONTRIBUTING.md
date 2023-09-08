# Contributing


## Coding Guidelines

### Data Hiding
Use encapsulation and data-hiding where possible.

This means:
- The scopes of variables/data should be reduced as much as possible.
- Avoid the use of globals.

### Preprocessor Usage
The pre-processor should _only_ be used for two things:

####  1. _Really_ basic macros
Macros are hard to debug.

#### 2. Conditional inclusion of header files where necessary for cross-platform code.
See the section on [Cross-platform support](#cross-platform-support).

### Cross-platform support
- All platform specific code should be in `platform/`.
- Do not use a platform specific functions and types outside of `platform/`
- Instead, create a cross-platform wrapper around it.
