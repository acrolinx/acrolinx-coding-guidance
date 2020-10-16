# Guidance for the Development of Acrolinx Integrations

## About This Document

The goal of this document is to have some kind of standard for developing code at Acrolinx.

This document is a collection of answers to questions that popped up in previous projects.
It's not complete. If you find something that should be added, please contribute. Please read this document carefully.
Even if you're keen to [start your new project](https://docs.acrolinx.com/customintegrations),
take the time to read it.
The Coding Guidance might save you a lot of trouble and time later.
That said, this document is no replacement for good education,
a stack of [good coding books](topics/coding-style.md),
or the experience and intuition that a good developer has.

You don't need to agree with all the points in this document,
and you might find exceptions where it makes sense to implement something differently.
Remember: There are good reasons to not do good things.
Make sure that your reasons are good enough. You're able to explain them, and
it's not just a personal attitude ;-).

This document is written primarily for developing Sidebar integrations at
Acrolinx. They interact with a writer and communicate with the
Acrolinx Platform. Some parts also apply for our Platform development as well as embedded integration development.

## Before You Start

Please contact [Acrolinx SDK support](topics/sdk-support.md) for consulting and getting your integration certified.

Make sure that your IDE and system are properly configured.

The Acrolinx default settings and templates can be found in this repository:

    git clone https://github.com/acrolinx/acrolinx-coding-guidance.git

Have a look at the [IDE Settings](ide-settings).

## [Proof of Concept](topics/poc.md)

## [Integration Points](topics/integration-points.md)

## [Project Setup](topics/project-setup.md)

## [Packaging](topics/packaging.md)

## [Coding Style](topics/coding-style.md)

## [Formatting](topics/formatting.md)

## [Interoperability](topics/interoperability.md)

## [Performance](topics/performance.md)

## [Design](topics/design.md)

## [Libraries](topics/libraries.md)

## [Logging](topics/logging.md)

## [Exception Handling](topics/exception-handling.md)

## [Localization L10N](topics/l10n.md)

## [Testing / Assertions](topics/testing.md)

## [Security and Safety](topics/security-safety.md)

## [Storing Data](topics/store-data.md)

## [Initialization](topics/initialization.md)

## [Text Extraction](topics/text-extraction.md)

## [Result Processing](topics/result.md)

## [Lookup](topics/text-lookup.md)

## [Authentication and Acrolinx URL Configuration](topics/configuration.md)

## Checklist

You may want to use the [Review Checklist for Acrolinx Integrations](topics/checklist.md) to ensure the standards.

## [Minimal Certification Requirements](topics/minimal-requirements.md)

## License

Copyright 2016-present Acrolinx GmbH

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at:

[http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

For more information visit: [https://www.acrolinx.com](https://www.acrolinx.com)
