# Testing / Assertions

1. Static code analysis should be performed. That is why you should use TypeScript, if you use JavaScript.
2. At least a couple of tests should run, at each build. They should ensure that:
    1. everything is wired correctly.
    2. the integration is able to run.
    3. no required libraries are missing.
    4. the [lookup](text-lookup.md) of issues within the original text works properly.
3. The tests of the [Test Sidebar](test-sidebar.md) must pass.
4. Use the [request validator](https://docs.acrolinx.com/kb/en/how-to-use-the-request-validator-13730818.html) (`<ACROLINX_SERVER:PORT>/request-validator/`)
   to verify what is sent to the Acrolinx Platform and that all information is filled out properly.
Manual testing is required for the cases that aren't covered by automated tests.

## Static Code Analysis

A linter helps identify possible bugs, and looking for potential problems like:

* unused code,
* complicated code,
* redundant code,
* code smells, and
* bad practices.

### JavaScript

Running a linting tool like:

* *JSHint*,
* *JSLint*, or
* *ESLint* at build time is mandatory.

### C\#

* Assertions or, better yet,
* contracts should be used.

### Java

* Use:
    + Annotations or,
    + assertions or,
    + Google Preconditions.

### C++

* Boost
* Use a memory leak detector.

### Objective-C

* Use [static analyzer and leak detection in XCode](https://help.apple.com/xcode/mac/8.0/#/devb7babe820).
* [OCLint](http://oclint.org/).

## Automated Unit / Integration Testing

### JavaScript

* Mocha
* Chai
* Karma

### C++

* Boost

### C\#

* Visual Studio Unit Testing Framework / MSTest
* Moq

### Java

* JUnit
* Mockito
* Hamcrest

### Objective-C

* XCTest / XCode