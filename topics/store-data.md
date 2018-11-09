# Storing Data

Integration stores data in the LocalStorage.
In-case accessing LocalStorage isn't possible then a custom settings store could be used.

## Types and Location

1. Windows Registry
2. .properties file
3. Host editor data store

In multiplatform integrations, where no built-in store is available it's preferred to write data to the user directory.

See also:
Acrolinx Storage in .NET [SDK](https://github.com/acrolinx/sidebar-sdk-dotnet/blob/master/README.md#sdk-features)
