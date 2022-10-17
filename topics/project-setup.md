# Project Setup

## Git

Use Git as a source code repository.
You can use either the Acrolinx internal Git setup or the Acrolinx organization on GitHub.

### Branches

The main development branch is `master`. It's used by default for building on Jenkins.
You can use other branches for feature development. Eventually, you must merge any feature branches to `master`.

### Branch Naming Conventions

* `feature/DEV-<XXXX>`
* `feature/<feature-name>`
* `exp/<my-experimental-stuff>`
* `private/<nobody-needs-to-look-at-this>`
* `release/<version_no>` - release branches, only if you have to work on it, otherwise use tags.

### Push to `master` Branch

The branch `master` must always be clean.
The source must compile and tests must pass before you can commit to the `master` branch.
If you want to share non-working code, use another branch.

### Checked-in Files

*Keep the repo clean!*

The repo must not contain any files created by the build process.
Only add these files to the repo if you cannot create them easily:

* compiled binary files
* IDE-specific files
* user-specific files

If you decide to use third-party libraries, don't check them in to the code base.
If possible, access libraries from a distribution site like Maven Central.
Use the appropriate dependency management tools (`Maven`, `Gradle`) that meet your needs.

Watch out for special operating system files and directories:

* `bin`
* `debug`
* `Thumbs.db`
* `.project`, the notorious
* `.DS_Store`

Never check in credentials or private keys.

Use the `.gitignore` file to ignore all unwanted files.

### Commits

Prefix Git commit messages with the JIRA ticket number. For example, use `DEV-<XXXX>`,
followed by a short comment that describes what you changed.
Add more details after an empty line. The scope of one commit is usually small enough
to describe the change in the title line.

```text
DEV-1234 Refactored check document method

- extracted transport format as separate parameter
- added tests for different parameters
```

Always commit formatting changes separately from code changes. That way you can easily identify code changes.
If you haven't pushed yet, use `git rebase` to keep our history clean.
Never rewrite public history.

### Hooks

We like to give customers the option of using Acrolinx in their preferred language.

* At Acrolinx, a native speaker of English approves the English source strings.
* Qualified translators translate the strings into the four target languages (German, Swedish, French and Japanese).
* A standard L10n workflow uses hooks to pull the latest translated strings as part of the integration build job.

Create a ticket for DevOps to get the L10n workflow set up for your project.

See: [Localization L10N](l10n.md)

## Coding Languages

Use the programming language that best suits the host editor and operating system.
If you can choose the language without any restrictions, we recommend JavaScript for its interoperability.
But we prefer TypeScript.

See the [Developer Tools](https://docs.acrolinx.com/customintegrations/api-sdks-and-samples)
for an overview of the supported technologies.

## Build System

### Naming

The name of the job in the build system should almost be the same as the lowercase [name of the package](packaging.md#packaging)
in:

* Use `<products>-<classic?>-<os>-<platform>` for the job that builds the integration:
    + Use `word-win-x86` for Word for Windows Sidebar Integration x86 version.
    + Use `word-mac` for Word for Mac Sidebar Integration all platforms.
    + Use `vscode` for a multiplatform version of an integration for Microsoft Visual Studio Code.
    + Use `word_powerpoint-win` for a job that creates several installers for Word and for PowerPoint.
    + Use `office-win` if you create a bundled package that installs multiple Microsoft Office integrations at once.
* Use `<product>-<classic?>-<platform>-deploy` for the job that deploys the latest package to an update side or live system.

### Description

For the project, use a short description that includes:

1. A short description of which components result from the build process, if it's not obvious from the name.
2. Names of the developers you can contact if the build breaks.
3. A description of the parameters that you can set in the build job.

### Build Steps

The standard build process has these steps:

1. Manage or download dependencies
2. Set build Number
3. Compile
4. Run tests
5. Minify or obfuscate
6. Package or build installer
7. Sign the package
8. Run integration tests
9. Deploy to development instance
10. (Manual testing)
11. Deploy release

### Build Tools

#### Java

If you're setting up a Java project, then use Gradle. Maven is also ok.
Use a template or parent provided by Acrolinx.
Use Spotless to help with code quality.

#### JavaScript

A recommended toolbox includes:

1. *npm* (bootstrapping dependency management)
2. *bower* or *npm* (for dependency management)
3. *grunt* (as task runner) Alternatives: *gulp*, *npm* scripts

Make sure that your project includes these steps:

* configured tasks to compile
* run tests
* run the application (if possible) and
* release or deploy the artifacts.

If you're using Grunt, the following tasks should be available:

* `grunt dist:release` should compile, run tests and package a release-ready artifact of the integration.
* `grunt deploy:dev` should deploy to an internal repo or update site.
* `grunt deploy:release` should deploy to:
    + a public repo
    + update site or
    + put the integration where someone can manually upload the artifact to MADAM (Acrolinx delivery tool).

#### C++

* Visual Studio 2015 .sln

#### C\#

* Visual Studio 2015 .sln
* NuGet

#### Objective-C or SWIFT

* XCode 7 compatible
* Create Specific Workspace: Don't let XCode do it for you.
* Set up projects with correct names and prefix: Use simple words and the prefix `ACRO`.
* Create an Ad hoc and App Store build configuration so that you can handle configuration for different destinations.
* Configure build setting to improve quality.

### Naming of the Integration

* The name of the Acrolinx Integration should be typically "Acrolinx for `<NAME_OF_HOST_EDITOR_OR_CMS>`"

## Version Information

Specify the version number at exactly one place in the integration code.
You should do this in the standard way for the language. The minor and major version number is Acrolinx product management.
If possible, use `major.minor.patch.build`

### JavaScript

Depending on the project, use `bower.json` or `package.json`.

### C++ or C\#

Use project settings and AssemblyInfo and the information must appear in the DLL info as well.

### Objective-C / SWIFT

Project settings in XCode (Info.plist)

## Readme

Add to the repo a `README.md` file that includes the following information:

1. How to build the source code automatically, preferably in a Jenkins environment
2. How to set up a development environment, including:
    1. Building
    2. Running
    3. Debugging
3. How to make and deploy a release build
4. How to install the integration into the host editor
5. Where to find the log files that the integrations writes. 

## License Information File

Add to the repo a file that includes all referenced libraries and their licenses.
Some tools might provide this information based on dependency management.
Don't forget to include dependencies of dependencies.
Choose an obvious file name like `LICENSES.md` or a name predefined by the tools that you use.
