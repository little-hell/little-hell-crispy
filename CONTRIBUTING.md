# Contributing


## Coding Guidelines

### Cross-platform support
- All platform specific code should be in `platform/`.
- Do not use a platform specific functions and types outside of `platform/`
- Instead, create a cross-platform wrapper around it.
