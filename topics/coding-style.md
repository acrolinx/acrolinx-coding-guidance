# Coding Style

Ordered by priority:

1. Readable / Understandable code
2. Build the simplest thing possible (this isn't always easy).
3. Make decisions and if you can't, keep asking questions until you can.
4. Avoid abstractions you don't need immediately.
5. Packages / namespaces / classes / functions should have names that explain what they do.
6. Stateless, try to avoid having a (mutable) state in your objects
7. Use immutable objects
8. Don't repeat yourself - avoid code duplication
9. Try to write object-oriented code or [functional programming](https://en.wikipedia.org/wiki/Functional_programming)
10. Comments are often a hint that your code isn't self-documenting - maybe you have to rename your method or variable.
11. Minimal documentations are mandatory:
    * What does the class do, which exceptions will it throw, which values does the method accept, why?
    * Even better, if this documentation is checked by:
        1. Compiler
        2. Annotations
        3. Assertions
12. You must not have compiler / JSHint warnings.
    If there are false warnings, add annotations / ignores for them, but don't ignore all warnings, comment your "ignores".
13. Document APIs using the platform-specific framework:
    * Javadoc
    * appledoc
    * etc.

## Java

If you aren't sure how to write good Java code, have a look at this book:

Robert C. Martin: Clean Code - A Handbook of Agile Software Craftsmanship

## JavaScript

* Avoid usage of "this". Often "this" doesn't point to the object you think.
  If you want to refer to "this" inside a function, you might be able to use a variable pointing to the object instead.
* Don't perform sync AJAX calls.

If you aren't sure how to write good JavaScript code, have a look at the [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript).

## C++

If you aren't sure how to write good C++ code, have a look at these books:

* Effective C++,
* Effective Modern C++, both by Scott Meyers

## Python

* In general, follow the PEP 8 guidelines.
* Python 3.x should be used if possible.
* In Python 2.x, prefer new-style classes must be used.

## Objective-C

* [Acrolinx Mac Coding Guidelines](mac-coding-guidelines.md)
