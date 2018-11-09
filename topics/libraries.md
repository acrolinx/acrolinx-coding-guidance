# Libraries

We want to make sure that we don't rebuild something that already exists.
If you need functionality that you guess someone must have implemented before,
try to find and reuse the existing implementation rather than reimplementing it yourself.

## Checking in Libraries

Usually, libraries shouldn't be checked in and a dependency management system should be used.
Exceptions are if a specific version is required and not deployable to internal npm/maven repos.

## Licensing

Make sure that the licenses of the used libraries are:

* compatible with commercial software development, and
* compatible with each other.

### Usually OK

* Public Domain,
* variants of BSD,
* Apache Software License,
* MIT,
* Creative Commons (BY, ND),
* Common Development and Distribution License,
* Mozilla Public License (MPL),
* Artistic License.

### Check Carefully

Please carefully consider the use of libraries with the following licenses:

* LGPL,
* GPL,
* Eclipse Public License,
* Creative Commons SA

### Usually Not OK

* AGPL,
* Creative Commons NC,
* Proprietary licenses

## Creating Own Libraries

Often it makes sense to share code between different projects.
Most of Acrolinx' integrations use the Sidebar and are able to run JavaScript code.
Thus, try to implement core components in JavaScript, so that they can be reused in several integrations across all platforms.

## Standard Libraries and Tools

Before creating a new library, make sure that the functionality isn't already covered by one of the following libraries.
The following libraries are often used by Acrolinx Integrations:

### JavaScript

* Npm
* Grunt
* Bower
* TypeScript
* JQuery
* Lodash
* Mocha
* Chai
* Karma
* QUnit

### C\#

* NuGet
* Newtonsoft.Json
* Moq
* log4net

### Java

* Log4j
* Google Guava
* JUnit
* Mockito
* Hamcrest

### C++

* Boost

### Objective-C

* Google Mac Toolbox