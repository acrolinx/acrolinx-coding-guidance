# Project Setup

## Git

The source code must be managed with Git.
Either our internal Git-setup or on GitHub in the Acrolinx organization must be used.

### Branches

The main development branch is `master`. It's used by default for building on Jenkins.
Other branches can be used for feature development. Feature branches must be merged to `master` after a while.

### Recommendation for Branch Names

* `feature/DEV-<XXXX>`
* `feature/<feature-name>`
* `exp/<my-experimental-stuff>`
* `private/<nobody-needs-to-look-at-this>`
* `release/<version_no>` - release branches, only if you have to work on it, otherwise use tags.

### Push to `master` Branch

The branch `master` must always be clean.
The source must compile and the test must pass before a commit to the master branch is allowed.
If you want to share nonworking code, use another branch.

### Checked-In Files

*Keep the repo clean!*

The repo must not contain any files created by the build process.
Only add the following files to the repo if they can't be easily created:

* compiled binary files,
* IDE-specific files, or
* user-specific files.

Libraries that are distributed in a standard way like Maven Central must not be checked in
but managed with the appropriate dependency management tools (`Maven`, `Gradle`, etc.).
Be aware of files and directories like:

* `bin`,
* `debug`,
* `Thumbs.db`,
* `.project`, the notorious
* `.DS_Store`, and so on.

Never ever check in credentials or private keys.

Use the `.gitignore` file to ignore all unwanted files.

### Commits

Git commit messages must start with the JIRA ticket number, for example, `DEV-<XXXX>`,
followed by a short comment that describes what was changed.
Further explanation can be added after an empty line.
Usually the scope of one commit should be small enough that the title line is enough to describe it.

```text
DEV-1234 Refactored check document method

- extracted transport format as separate parameter
- added tests for different parameters
```

Formatting changes should be committed separately from code changes. Then code changes are easy to identify,
and aren't hidden in noise.
If you haven't pushed yet, use `git rebase` to keep our history clean.
Never ever rewrite public history.

### Hooks

We like to give customers the option to use Acrolinx in their preferred language.
A native English speaker approves the English source strings,
and qualified translators translate them into the four auxiliary languages (German, Swedish, French and Japanese).
We have a standard L10n workflow that uses hooks to pull the latest translated strings as part of the integration build job.
Create a ticket for DevOps to get the L10n workflow set up for your project.

See: [Localization L10N](l10n.md)

## Coding Languages

The integration must be created in the language that best suits the host editor and operating system.
If the language for a component can be chosen without any restrictions, JavaScript-based is preferred because of its interoperability.
TypeScript is preferred.

See the [Developer Tools](https://docs.acrolinx.com/customintegrations/api-sdks-and-samples)
article for an overview of the supported technologies.

## Build System

### Naming

The name of the job in the build system should almost be the same as the lowercase [name of the package](packaging.md#packaging)
in:

* Use `<products>-<classic?>-<os>-<platform>` for the job that builds the integration, like:
    + Use `word-win-x86` for Word for Windows Sidebar edition x86 version.
    + Use `word-win-classic-x86` for Word for Windows Classic edition x86 version.
    + Use `word-mac` for Word for Mac Sidebar edition all platforms.
    + Use `vscode` for a multiplatform version of an integration for Microsoft Visual Studio Code.
    + Use `word_powerpoint-win` in case you have one job creating several installers for Word and for PowerPoint.
    + Use `office-win` in case you create a bundled package that installs multiple Microsoft Office integrations at once.
* Use `<product>-<classic?>-<platform>-deploy` for the job that deploys the latest package to an update side or live system.

### Description

The project should have a short description. The description contains:

1. A short description which components will be build in case it's not 100% clear from the used name,
2. The names of the developers who can be asked in case the build is broken,
3. A description of the parameters that can be set in the build job.

### Build Steps

The standard build setup contains the following steps:

1. Manage / download dependencies
2. Set build Number
3. Compile
4. Run tests
5. Minify / obfuscate
6. Package / build installer
7. Sign the package
8. Run integration tests
9. Deploy to development instance
10. (Manual testing)
11. Deploy release

### Build Tools

#### Java

A typical Java project should be set up with Gradle. Maven is also ok.
A provided template/parent from Acrolinx should be used.
Spotless is used to ensure code quality.

#### JavaScript

A recommended toolbox is:

1. *npm* (bootstrapping dependency management)
2. *bower* or *npm* (for dependency management)
3. *grunt* (as task runner) Alternatives: *gulp*, *npm* scripts

The project should contain configured tasks to compile, run tests,
run the application (if possible) and release/deploy the artifacts.

For example in case of Grunt the following tasks should be available:

* `grunt dist:release` should compile, run tests and package a release-ready artifact of the integration.
* `grunt deploy:dev` should deploy to an internal repo or update site.
* `grunt deploy:release` should deploy to:
    + a public repo, or
    + update site, or
    + put the integration to some place where the artifact can be uploaded manually to MADAM (Acrolinx delivery tool).

#### C++

* Visual Studio 2015 .sln

#### C\#

* Visual Studio 2015 .sln
* NuGet

#### Objective-C / SWIFT

* XCode 7 compatible
* Create Specific Workspace: Don't let XCode do it for you.
* Set up projects with correct names and prefix: Use simple words and the prefix `ACRO`.
* Create Ad hoc and App Store build configuration so that you can handle configuration for different destinations.
* Configure build setting to improve quality.

### Naming of the Integration

* The name of the Acrolinx Integration should be typically "Acrolinx for `<NAME_OF_HOST_EDITOR_OR_CMS>`"

## Version Information

Specify the version number at exactly one place in the integration code.
You should do this in the standard way for the language. The minor and major version number is Acrolinx product management.
If possible, use `major.minor.patch.build`

### JavaScript

Depending on the project, `bower.json` or `package.json` should be used.

### C++ / C\#

Project settings / AssemblyInfo should be used and the information must appear in the DLL info as well.

### Objective-C / SWIFT

Project settings in XCode (Info.plist)

## Readme

The repo must contain a `README.md` file that contains the following information:

1. How to build the source code automatically, preferably in a Jenkins environment
2. How to set up a development environment including
    1. Building
    2. Running
    3. Debugging
3. How to make/deploy a release build.
4. How to install the integration into the host editor
5. Where to find the log files produced by the integration

## License Information File

The repo must contain a file that contains all referenced libraries and their licenses.
There might be tools that provide this information based on dependency management.
Make sure that you also catch dependencies of dependencies.
The name of the file must be obvious, for example `LICENSES.md`, or predefined by the tools that are used.