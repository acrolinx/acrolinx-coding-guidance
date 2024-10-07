# Storing data

Your integration stores data in the LocalStorage.
If it's not possible to access LocalStorage, then you can use a custom settings store.

## Types and location

1. Windows Registry
2. .properties file
3. Host editor data store

In multiplatform integrations, where no built-in store is available, then write data to the user directory.

See also:
Acrolinx storage in .NET [SDK](https://github.com/acrolinx/sidebar-sdk-dotnet/blob/master/README.md#sdk-features)
