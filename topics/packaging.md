# Packaging

A build script must be provided that creates a ready-to-install artifact.
Make sure that:

1. the package has a name matching the pattern:
    * `<product>V<version>_B<build>.<platform>.<extension>` like
        + `WordV4.6_B15.32_bit.msi`, or
        + `AEMV4.5_B25.zip`.
2. version and build information are set correctly.
   (Version must be configured in one place and checked in, build comes from Jenkins.)
3. the signature is hard-coded and set correctly according to the integration.
4. code is minified and obfuscated - or we explicitly decided not to do that.
5. referenced libraries are included - don't reference external pages, like [CDNs](https://en.wikipedia.org/wiki/Content_delivery_network).
6. license files of referenced libraries are included.
7. the package is signed. Acrolinx has a valid certificate that should be used on Jenkins.
   Don't use it on developer computers and don't be checked into the project's version control.
8. the package is ready to install.

## Host Editor with Update Site

If the host editor supports installing integrations via an update site, this kind of delivery should be the goal.
If it's possible to install from a private update site, `http://updates.acrolinx.com` should be used for this.
If only a public marketplace or other kind of repository is available, we have to decide, if we want to push it public.
Otherwise we might use some OS-specific installer.

### Windows

 A signed MSI installer must be provided.

### Mac

A signed DMG must be provided.

### Java

A signed JAR must be provided.

## Uninstall

* Each installer must have an uninstall routine.
* The uninstall must remove the installation files.
* Custom user settings should stay on the computer (exception: they consume too much disk space).

## Upgrade

While building an installer, keep in mind that later an upgrade might be provided.
Make sure that a proper uninstall is provided and that the installer will be aware of
previous or upcoming installations.
To achieve a smooth upgrade especially naming and a clear versioning is important.