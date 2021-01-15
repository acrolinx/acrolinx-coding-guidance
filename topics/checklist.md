# Review Checklist for Acrolinx Integrations

The goal of this checklist is to ensure a standard for developing code at Acrolinx.

Some of these items are features that developers have to implement to successfully build an integration.
Some functional requirements are implemented without any additional work if you clone from a sample or template project.
Other items on this checklist are nonfunctional requirements that
developers should keep in mind all the time while developing.

## Certification

In case of certification make sure to minimally fulfill the [minimal certification requirements](sdk-support.md#minimal-certification-requirements).

## How to Work with the Checklist

1. Copy this checklist to your source code repository of the integration you're currently working on.
2. When you finish a feature on this list, you should change the state of the checkbox from unchecked `[ ]` to checked `[x]`.
3. At the end of an iteration, go through this list and tick the checkboxes of the implemented features.
4. Some items might turn out to require more effort. In this case, it makes sense to create a (Jira) ticket.
5. The [Symbols](#symbol-description) will help you understand if each item is relevant for your project.
   It helps you decide which role is best suited for a correct implementation.
6. The description might be a bit too short to provide all the information you need.
 The title of each section links to a more detailed Coding Guidance topic.
7. Before you release the integration, ensure that all checkboxes are checked [x] to have a release protocol.
8. Before you start a new iteration, make sure that you clone the latest copy of this checklist.
 Also, uncheck all nonfunctional items on this list.

### Symbol Description

#### Item Relevance for Different Integration Types

![Custom Integration](images/custom.png) Important for **custom** Acrolinx Integrations

![Acrolinx Integration](images/acrolinx.png) Important for **standard** Acrolinx Integrations

#### Who Ensures the Correctness

![Developer](images/developer.png) A **developer** reviews the code.

![QA](images/qa.png) A **QA** person validates the functionality.

## [Integration Points](integration-points.md)

* [ ] The integration integrates at the correct points.
* [ ] The correct [check type](check-types.md) is used.

## [Project Setup](project-setup.md)

* Git is properly used.
    + [ ] Main branch is `master`.
          ![Acrolinx Integration](images/acrolinx.png) ![Developer](images/developer.png)
    + [ ] `master` branch is stable.
          ![Acrolinx Integration](images/acrolinx.png)![QA](images/qa.png)
    + [ ] Unwanted (binary) files aren't checked-in and ignored using `.gitignore`.
          ![Acrolinx Integration](images/acrolinx.png) ![Developer](images/developer.png)
    + [ ] No passwords are checked in.
          ![Acrolinx Integration](images/acrolinx.png) ![Developer](images/developer.png)
    + [ ] Commits start with ticket number.
          ![Acrolinx Integration](images/acrolinx.png) ![Developer](images/developer.png)
    + [ ] Transifex hooks are set up.
          ![Acrolinx Integration](images/acrolinx.png) ![Developer](images/developer.png)
* [ ] Best [coding language / SDK](https://docs.acrolinx.com/customintegrations/api-sdks-and-samples) has been chosen.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![Developer](images/developer.png)
* An automatic build is in place.
    + [ ] The job name matches the pattern `<products>-<classic?>-<os>-<platform>`.
          ![Acrolinx Integration](images/acrolinx.png)![Developer](images/developer.png)![QA](images/qa.png)
    + The job description contains:
        - [ ] Which components are built?
              ![Acrolinx Integration](images/acrolinx.png)![Developer](images/developer.png)![QA](images/qa.png)
        - [ ] Which developers are responsible for this project?
              ![Acrolinx Integration](images/acrolinx.png)![Developer](images/developer.png)![QA](images/qa.png)
        - [ ] Which build job parameters can be set?
              ![Acrolinx Integration](images/acrolinx.png)![Developer](images/developer.png)![QA](images/qa.png)
    + Build contains the following steps:
        - [ ] Manage / download dependencies.
              ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)![Developer](images/developer.png)
        - [ ] Set the build number.
              ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
        - [ ] Compile
              ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![Developer](images/developer.png)
        - [ ] Run tests.
              ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
        - [ ] Minify or obfuscate code.
              ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
        - [ ] Package and build installer.
              ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
        - [ ] Sign the package.
              ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
        - [ ] Run integration tests.
              ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
        - [ ] Deploy to development instance.
              ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
        - [ ] \(Do manual testing.\)
              ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
        - [ ] Deploy or ship the release.
              ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
* [ ] Version information uses the pattern `major.minor.patch.build`.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
    + [ ] JavaScript: bower.json or package.json is updated.
          ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![Developer](images/developer.png)
    + [ ] C++ / C#: Project settings / AssemblyInfo should be used and the information must appear in the DLL info as well.
          ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![Developer](images/developer.png)
    + [ ] Objective-C / SWIFT: Project settings in XCode (Info.plist)
          ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![Developer](images/developer.png)
* A `README.md` in the project root contains the following information:  
    + [ ] How to build the source code automatically, preferably in a Jenkins environment
          ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![Developer](images/developer.png)
    + How to set up a development environment including:
        - [ ] Building
              ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![Developer](images/developer.png)
        - [ ] Running
              ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![Developer](images/developer.png)
        - [ ] Debugging
              ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![Developer](images/developer.png)
    + [ ] How to install the integration into the host editor
          ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
    + [ ] Where to find the log files generated by the integration
          ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
* [ ] The repo contains a license information file that contains the names of referenced libraries and their licenses.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)

## [Packaging](packaging.md)

* Provide a build script that creates a ready-to-install artifact. Make sure that:
    + [ ] The package has a name matching the pattern `<product>V<version>_B<build>.<platform>.<extension>`.
          ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
    + [ ] Version and build information are set correctly.
      (Version must be configured in one place and checked in, build comes from Jenkins.)
          ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
    + [ ] The signature is hard-coded and set correctly according to the integration.
          ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
          ![Developer](images/developer.png) ![QA](images/qa.png)
    + [ ] The signature is the same for all parts of the integration, automated as well as interactive.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
          ![Developer](images/developer.png) ![QA](images/qa.png)
    + [ ] Code is minified and obfuscated - or we explicitly decided not to do that.
          ![Acrolinx Integration](images/acrolinx.png) ![QA](images/qa.png)
    + [ ] Referenced libraries are included - don't reference external pages, like [CDNs](https://en.wikipedia.org/wiki/Content_delivery_network).
          ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
          ![Developer](images/developer.png) ![QA](images/qa.png)
    + [ ] License files of referenced libraries are included.
          ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
    + [ ] The package is signed. Acrolinx has a valid certificate that should be used on Jenkins.
          Don't use certificates on developer computers.
          Don't check certificates into the project's version control.
          ![Acrolinx Integration](images/acrolinx.png) ![QA](images/qa.png)
    + [ ] The package is ready to install.
          ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
* [ ] The package is deployed to the host editor with an update site or a marketplace.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
* [ ] Windows: Provide a signed MSI installer.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
* [ ] Mac: Provide a signed DMG.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
* [ ] Java: Provide a signed JAR.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
* [ ] The installer provides an uninstall functionality.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
* [ ] The installer provides an upgrade functionality.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)

## [Coding Style](coding-style.md)

* [ ] Code is readable and understandable.
      ![Acrolinx Integration](images/acrolinx.png) ![Developer](images/developer.png)
* [ ] Build the simplest thing possible (this isn't always easy).
      ![Acrolinx Integration](images/acrolinx.png) ![Developer](images/developer.png)
* [ ] Avoid abstractions you don't immediately need.
      ![Acrolinx Integration](images/acrolinx.png) ![Developer](images/developer.png)
* [ ] Packages / namespaces / classes / functions should have names that explain what they do.
      ![Acrolinx Integration](images/acrolinx.png) ![Developer](images/developer.png)
* [ ] Stateless - try to avoid having any (mutable) state in your objects.
      ![Acrolinx Integration](images/acrolinx.png) ![Developer](images/developer.png)
* [ ] Use immutable objects.
      ![Acrolinx Integration](images/acrolinx.png) ![Developer](images/developer.png)
* [ ] Don't repeat yourself - avoid code duplication.
      ![Acrolinx Integration](images/acrolinx.png) ![Developer](images/developer.png)
* [ ] Try to write object-oriented code or [functional programming.](https://en.wikipedia.org/wiki/Functional_programming)
      ![Acrolinx Integration](images/acrolinx.png) ![Developer](images/developer.png)
* [ ] Comments are often a hint that your code isn't self-documenting, maybe you have to rename your method or variable.
      ![Acrolinx Integration](images/acrolinx.png) ![Developer](images/developer.png)
* [ ] Minimal documentations are mandatory:
      What does the class do, which exceptions will it throw, which values does the method accept.
      ![Acrolinx Integration](images/acrolinx.png) ![Developer](images/developer.png)
* [ ] You must not have compiler / JSHint warnings.
      If there are false warnings, add annotations / ignores for them, but don't ignore all warnings.
      Comment why you ignored files. ![Acrolinx Integration](images/acrolinx.png) ![Developer](images/developer.png) ![QA](images/qa.png)

## [Formatting](formatting.md)

* [ ] The source code is formatted properly.
      ![Acrolinx Integration](images/acrolinx.png) ![Developer](images/developer.png)
* [ ] The copyright header is in all source code files.
      ![Acrolinx Integration](images/acrolinx.png) ![Developer](images/developer.png)

## [Interoperability](interoperability.md)

* [ ] Path separation `/` and `\` and `:` and `¥` - in Java you often can just use the `/`.
      See: [Representations of paths by operating system and shell](https://en.wikipedia.org/wiki/Path_%28computing%29#Representations_of_paths_by_operating_system_and_shell)
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)
* [ ] Drive letter, root directories, UNC, and network paths
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)
* [ ] Interoperable command shell parameters
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)
* [ ] New lines `\n`, `\r`, `\r\n` - if you can choose, use `\n`.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)
* [ ] Calendar / Time format `2016-03-31 19:30` vs. `31.03.16 19:30` vs. `03/31/2016 01:31 a.m.`
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)
    + [ ] Internal log files should use ISO date like `2016-03-30T11:54:33.986Z`.
          ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
    + [ ] If displayed to the end user, the system locale should be used.
          ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
* [ ] Encoding UTF-8 is preferred. Use UTF-8 internally, the Acrolinx Platform requires it.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![Developer](images/developer.png)
* [ ] Some languages typically don't have spaces as word boundaries, for example Japanese.
      Other languages have strange characters like German `äöü`, Spanish punctuation like `¡` and `¿`,
      or different behavior on the upper/lower casing like Turkish `ı` → `I`, `i` → `İ` instead of `i` → `I`.
      Some languages have right-to-left writing.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)
* [ ] Encoding of entities `&` and `&amp;` in HTML and XML
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)
* [ ] Locale-aware collation order while sorting. See: [Collation](https://en.wikipedia.org/wiki/Collation)
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
* [ ] JavaScript: Your code should be able to run in all typical web browsers:
      Chrome, Safari, Internet Explorer, Microsoft Edge, Firefox – version and test scopes must be agreed project wise.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)
* [ ] C#: The code must be compatible with Microsoft.Net and Mono.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![Developer](images/developer.png)
* [ ] Java: The code must run with the latest Oracle JRE and IBM JRE, both 32-bit and 64-bit.
      It must also run in the VMs typically used by the host editor.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
* [ ] C++: Write code that compiles with gcc on Linux as well.
      If there's a library or Windows function and you're developing for Windows, use it.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![Developer](images/developer.png)
* [ ] Objective-C: OS X version support discussed with product management.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)

## [Performance](performance.md)

* [ ] User actions complete within 200 ms.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
* [ ] If they're slower, try to optimize your code.
      If you can't get under that threshold, display some kind of progress status.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
* [ ] The application must not hang at any point.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)

## [Design](design.md)

* [ ] Make sure that the design is suitable for the host editor, operating system, and Acrolinx standards.
      If necessary, the Acrolinx Design Team will provide designs for dialogs.
      If you have trouble implementing the design or user experience, discuss it with the Acrolinx Design Team.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)

## [Libraries](libraries.md)

* [ ] Ensure licensing of libraries that are used.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
    + Usually OK
        - Public Domain,
        - Variants of BSD,
        - Apache Software License,
        - MIT,
        - Creative Commons (BY, ND),
        - Common Development and Distribution License,
        - Mozilla Public License (MPL),
        - Artistic License.
    + Check carefully - Please carefully consider the use of libraries with the following licenses:
        - LGPL,
        - GPL,
        - Eclipse Public License,
        - Creative Commons SA
    + Usually not OK
        - AGPL,
        - Creative Commons NC,
        - Proprietary licenses
* [ ] Libraries of code that you create, which will be shared and reused in other projects.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![Developer](images/developer.png)
* [ ] Standard libraries and tools are used other libraries are carefully decided.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![Developer](images/developer.png)

## [Logging](logging.md)

* [ ] Some kind of logging exists.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
* [ ] Log types are used correctly.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)
* [ ] Start page shows logging information.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
* [ ] *Info level* logging is turned on by default.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
* [ ] Log format is: `<ISO-DATE-WITH-TIME> | [<LOG-LEVEL>] <CLASS-OR-MODULE>: <MESSAGE>`
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
* [ ] Path and filename are: `%TEMP%/acrolinx/logs/ISODATE-INTEGRATIONNAME.INSTANCEID.log`
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
* [ ] Sensitive data isn't logged.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)

## [Exception Handling](exception-handling.md)

* [ ] Don't have empty catch blocks
      (exception: if you're 290.3% sure that nobody is interested in the exception and everything is fine).
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![Developer](images/developer.png)
* [ ] Unexpected exceptions should be logged exactly once per occurrence or action.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)
* [ ] Unexpected exceptions can print a stack trace to the log (Error, not Warning).
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)
* [ ] No exception or edge case should crash the application.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)
* [ ] Prefer unchecked exceptions over checked exceptions.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![Developer](images/developer.png)
* [ ] Avoid error messages to the user.
      Often there are other solutions to prevent the integration running into an error situation at all.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)

## [Localization L10N](l10n.md)

* [ ] The UI language set in the host editor determines which UI language is displayed in the Acrolinx Integration.
      ![Acrolinx Integration](images/acrolinx.png) ![QA](images/qa.png)
* [ ] Fall back to English in case translation isn't present.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)
* [ ] The Transifex configuration file `.transifex` is present.
      ![Acrolinx Integration](images/acrolinx.png) ![Developer](images/developer.png)
* [ ] Key-Name conventions are used.
      ![Acrolinx Integration](images/acrolinx.png) ![Developer](images/developer.png)

## [Testing / Assertions](testing.md)

* [ ] Static code analysis should be performed. ![Acrolinx Integration](images/acrolinx.png) ![Developer](images/developer.png)
* A couple of tests should run at each build. They should ensure that:
    + [ ] Everything is wired correctly.
          ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![Developer](images/developer.png)
    + [ ] The integration is able to run.
          ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![Developer](images/developer.png)
    + [ ] No required libraries are missing.
          ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![Developer](images/developer.png)
    + [ ] The [lookup](text-lookup.md) of issues within the original text works properly.
          ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![Developer](images/developer.png)
* [ ] The tests of the [Test Sidebar](test-sidebar.md) must pass.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
* [ ] Use the [request validator](https://docs.acrolinx.com/kb/en/how-to-use-the-request-validator-13730818.html)
      (`<ACROLINX_SERVER:PORT>/request-validator/`)
      to verify what is sent to the Acrolinx Platform and that all information is filled out properly.
      ![Acrolinx Integration](images/acrolinx.png) ![Custom Integration](images/custom.png) ![QA](images/qa.png)
* [ ] Manual testing is required for the cases, which aren't covered by automated tests.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png) ![QA](images/qa.png)
* [ ] JavaScript: *JSHint*, *JSLint*, or *ESLint* at build time is mandatory.
      ![Acrolinx Integration](images/acrolinx.png) ![Developer](images/developer.png)
* [ ] C#: Assertions or, better yet, contracts should be used.
      ![Acrolinx Integration](images/acrolinx.png) ![Developer](images/developer.png)
* [ ] Java: If you can't ensure correct usage by annotations, use assertions or, better yet, Google Preconditions.
      ![Acrolinx Integration](images/acrolinx.png) ![Developer](images/developer.png)
* [ ] C++: Boost, and a memory leak detector is used.
      ![Acrolinx Integration](images/acrolinx.png) ![Developer](images/developer.png)
* [ ] Objective-C: Use leak detection in XCode.
      ![Acrolinx Integration](images/acrolinx.png) ![Developer](images/developer.png)

## [Security and Safety](security-safety.md)

* [ ] Acrolinx Integrations must not cause the host application to crash.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)
* [ ] Avoid typical security issues like the [OWASP Top Ten](https://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project).
      ![Acrolinx Integration](images/acrolinx.png)
      ![Custom Integration](images/custom.png) ![Developer](images/developer.png) ![QA](images/qa.png)
* [ ] Avoid injection / cross-site scripting.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)
* [ ] Specifically, be careful inserting strings into HTML when doing replacements.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)
* [ ] SSL / TLS:  If you connect to a secure server, validate the certificate.
      Don't fall back to insecure connections if the connection fails.
      Example: if the user specifies `https://acrolinx.com`, don't automatically try `http://acrolinx.com`.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)
* [ ] SSL / TLS:  Make sure that you don't change the VM or system security settings to a less secure setting.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)
* [ ] Ensure that no passwords are stored.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)
* [ ] If you use an [SSO reverse proxy](https://github.com/acrolinx/acrolinx-proxy-sample) for authentication,
      make sure that the authentication is implemented securely in the proxy.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)
* [ ] If you open a URL, make sure that it starts with `https?://` (prevent remote code execution).
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png)
* [ ] Make sure that the integrations can connect production Acrolinx Platform cloud instances.
      Support for TLS 1.2, and other security settings.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png)

## [Initialization](initialization.md)

* [ ] The `clientComponents` are properly filled.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)

## [Text Extraction](text-extraction.md)

* [ ] Host Application with Underlying XML/HTML Format uses this format for checking.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)
* [ ] Make sure that you set the right format for checking.
      Are you using a multiformat editor? Have you considered using `auto` as format?
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)
* [ ] Make sure that you send the file name, URI, or a unique reference to your source document.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)
* [ ] DOCTYPE and/or root element names are set.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)
* Host Application API with Object Model:
    + [ ] DOCTYPE is properly set so that a [Content Profile](https://docs.acrolinx.com/coreplatform/latest/en/guidance/content-profiles/get-started-with-content-profiles)
      can be selected on the Acrolinx Platform side.
    + [ ] Keep the structure of the original object model.
          ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
          ![Developer](images/developer.png) ![QA](images/qa.png)
    + [ ] Keep the context information like: Title, Header, Paragraph, Table, ...
          ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
          ![Developer](images/developer.png) ![QA](images/qa.png)
* [ ] A clear has been made if check selection should be supported.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)

## [Result Processing](result.md)

* [ ] Decide whether you want to implement the Embed Check Data feature.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)

## [Lookup](text-lookup.md)

* [ ] The right lookup strategy is used and works, or the integration is just set to [read only](https://cdn.rawgit.com/acrolinx/acrolinx-sidebar-demo/v0.3.52/doc/pluginDoc/interfaces/_src_acrolinx_libs_plugin_interfaces_.initparameters.html#readonlysuggestions).
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)

## [Authentication and Server Configuration](configuration.md)

Make sure:

* [ ] the right strategy for populating the Acrolinx URL is used.
      ![Acrolinx Integration] (images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA] (images/qa.png)
* [ ] you implemented the best user authentication approach.
      Is some single sign-on, federate authentication, or just an external authentication required?
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)
* [ ] that no hard-coded username is used for checks from different users.
      ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png) ![QA](images/qa.png)

## [Scheduling](scheduling.md)

* [ ] A good [scheduling](scheduling.md) is implemented. ![Acrolinx Integration](images/acrolinx.png)![Custom Integration](images/custom.png)
      ![Developer](images/developer.png)
