# Formatting

The Acrolinx standard formatting and code style templates should be applied.
If they don't exist, you should code how the vendor of the language suggests.

## Formatter Settings, Save Actions, Templates

The Acrolinx default settings can be found in this repository.

### Header

Source files written by an Acrolinx team member must contain the Acrolinx copyright header:

```java
/* © CreationYear - present Acrolinx GmbH */
/* Copyright CreationYear - present Acrolinx GmbH */

/* © 2015 - present Acrolinx GmbH */
/* Copyright 2019 - present Acrolinx GmbH */
```

* "2015" is the year when the file was created.
* Use it in open source as well as closed source files.
* Obviously only for files that allow comments or another suitable construct to add a copyright header.
* Whenever you make significant changes to a file, you _can_ add the year to this line either with a comma or as a range.
* The form using '-present' is most convenient as it 'updates' automatically. It's unclear if this hold up in court.
* Don't put too much effort into the maintenance of the latest year!
  It determines the end of the copyright claim and we'll hardly use those files more than 50 years from now.
* This is mainly interesting for files that have 'significant' content.
  It doesn't hurt to put the copyright header into insignificant files. Examples:
    + A simple implementation of an interface: not significant
    + A bean with just getters and setters: not significant
    + some business logic: significant
    + an implementation of an algorithm: significant

## JavaScript

[www.w3schools.com/js/js_conventions.asp](http://www.w3schools.com/js/js_conventions.asp)

The integration shouldn't be exposed to the global namespace.
Use `acrolinx.<HOST_EDITOR_NAME>`, make sure that you don't override other Acrolinx components.

## C\#

[msdn.microsoft.com/en-us/library/ff926074.aspx](https://msdn.microsoft.com/en-us/library/ff926074.aspx)

The namespace should be `Acrolinx.<HOST_EDITOR_NAME>.<MODULE_NAME>`.

## Java

### Eclipse

Use Eclipse settings for [compiler settings](/ide-settings/java/eclipse/acrolinxJavaCompilerPreferences.epf),
[formatting](/ide-settings/java/eclipse/acrolinxJavaSourceFormat.xml),
[save actions](/ide-settings/java/eclipse/acrolinxJavaSourceCleanUp.xml),
[import order](/ide-settings/java/eclipse/eclipse.importorder),
and [templates](/ide-settings/java/eclipse/acrolinxJavaTemplates.xml), which are provided by Acrolinx.

Package name should be `com.acrolinx.client.<sidebar/classic>.<HOST_EDITOR_NAME>.<MODULE_NAME>...`.

### Gradle

For Gradle, you can use the [Gradle Spotless Plugin](https://plugins.gradle.org/plugin/com.diffplug.gradle.spotless).

* Add the content of the [build.gradle](/gradle-spotless-settings/build.gradle) to your projects root build file.
* Copy the files for [formatting](/gradle-spotless-settings/spotless.eclipseformat.xml),
  [import order](/gradle-spotless-settings/spotless.importorder),
  and [license header](/gradle-spotless-settings/spotless.license.java) into your projects root folder.

Make sure to adjust the [license header](/gradle-spotless-settings/spotless.license.java) to contain the right year.

Your build will fail if your code contains any format violations.
You can run `gradle spotlessApply` to get those fixed.

## Objective-C

* [Acrolinx Mac Coding Guidelines](mac-coding-guidelines.md)

1. Install [Clang formatter](https://github.com/travisjeffery/ClangFormat-Xcode/ ) for XCode 8+. Not required for XCode 7.
2. Use this [Acrolinx ClangFormat file](/ide-settings/objective-c/xcode/.clang-format)
   to apply the formatting changes to the code.
3. [Detailed ClangFormat Instructions](https://github.com/travisjeffery/ClangFormat-Xcode/blob/master/README.md)

## C++

[gist.github.com/lefticus/10191322](https://gist.github.com/lefticus/10191322)

## Markdown

Use the [markdownlint](https://github.com/DavidAnson/markdownlint) and apply the [configuration](/.markdownlint.json).

The differences to the standard configurations are:

* [MD004 - Unordered list style](https://github.com/DavidAnson/markdownlint/blob/v0.11.0/doc/Rules.md#md004)
  is set to `sublist`, since it's more readable and clear if sub lists have different bullet styles than the main list.
* [MD007 - Unordered list indentation](https://github.com/DavidAnson/markdownlint/blob/v0.11.0/doc/Rules.md#md007)
  is set to 4.
* [MD013 - Line length](https://github.com/DavidAnson/markdownlint/blob/v0.11.0/doc/Rules.md#md013)
  is set to 120 according to the Java line length. It's disabled for tables.
* [MD024 - Multiple headings with the same content](https://github.com/DavidAnson/markdownlint/blob/v0.11.0/doc/Rules.md#md024)
  is only forbidden for siblings.
* [MD026 - Trailing punctuation in heading](https://github.com/DavidAnson/markdownlint/blob/v0.11.0/doc/Rules.md#md026)
  is configured to allow question marks.
* [MD038 - Spaces inside code span elements](https://github.com/DavidAnson/markdownlint/blob/v0.11.0/doc/Rules.md#md038)
  is allowed. A lot of lookup examples need to talk about spaces.
