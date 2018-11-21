# Interoperability

The integration should work on different operating systems and with different processor architectures, including on VMs.

Keep in mind that different systems and locales require special handling.
The world as you're used to might be different in another country. Typical issues are:

1. Path separation `/` and `\` and `:` and `¥` - in Java you often can just use the `/`.
   See: [Representations of paths by operating system and shell](https://en.wikipedia.org/wiki/Path_%28computing%29#Representations_of_paths_by_operating_system_and_shell)
2. Drive letter, root directories, UNC, and network paths
3. Command shell parameters: If your integration, or build script calls a shell command, escape the parameters correctly.
   The parameter of `command **/*.xyz` will reach the command on Windows only.
   Most Linux shells resolve the `*`, before it reaches the command. The command won't work properly.
   If you escape the parameter using single quotes `'**/*.xyz`, it only works on Linux.
   On Windows, the single quote will be treated as part of the file name and no file will be found.
   Use the following interoperable form: `conmmand "**/*.xyz"`, where double quotes are used.
4. On Windows, lower and uppercase paths are the same. Keep that in mind in case you compare strings containing paths.
5. New lines `\n`, `\r`, `\r\n` - if you can choose use `\n`.
6. Calendar / Time format `2016-03-31 19:30` vs. `31.03.16 19:30` vs. `03/31/2016 01:31 a.m.`
    1. Internal log files should use ISO date like `2016-03-30T11:54:33.986Z`.
    2. If displayed to the end user, the system locale should be used.
7. Encoding UTF-8 is preferred. Use UTF-8 internally, the Acrolinx Platform requires it.
8. Some languages typically don't have spaces as word boundaries, for example Japanese.
   Other languages have strange characters like German `äöü`,
   Spanish punctuation like `¡` and `¿`,
   or different behavior on upper/lower casing like Turkish `ı` → `I`, `i` → `İ` instead of `i` → `I`.
   Some languages have right-to-left writing.
9. Encoding of entities `&`  and `&amp;` in HTML and XML
10. Locale-aware collation order while sorting.
   See: [Collation](https://en.wikipedia.org/wiki/Collation)

There are good reasons to write specific code for something:
Split your code into locale-specific parts and generic interoperable parts.
Especially on GUI implementation, you'll face this issue.
If you split a project into two pieces from the beginning, it will often cost less.
Having to identify specific and generic parts of your source code at the end of the project is usually expensive.

If interoperability is very expensive, we have to decide on the target platform project wise.

## JavaScript

Your code should be able to run in all typical web browsers:
Chrome, Safari, Internet Explorer, Microsoft Edge, Firefox – version and test scopes must be agreed project wise.

## C\#

The code must be compatible with Microsoft.Net and Mono.

## Java

The code must run with the latest Oracle JRE and IBM JRE, both 32-bit and 64-bit.
It must also run in the VMs typically used by the host editor.

## C++

Write code that compiles with gcc on Linux as well. But don't rebuild something that already exists.
If there's a library or Windows function and you're developing for Windows, use it.

Consider whether Qt might be an option for your project.

## Objective-C

Product Management supported versions of OS X.
