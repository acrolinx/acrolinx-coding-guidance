# Logging

In case of a crash or malfunction,
all integrations must write log messages.
The messages must enable support to figure out what went wrong.

## Types

Use the following log types:

1. **Trace/Extended/Debug:** entering an important method. Examples:
    * Events,
    * `check`,
    * `showOptions`,
    * `selectRange`,
    * `replaceRange`,
    * `documentOpened`,
    * `documentClosed`,
    * `activeDocumentChanged` (not `textChange`), …
2. **Normal/Info:** actions like check or application start/exit.
3. **Warning:** something went wrong, but the program can handle it and the user can use the UI to react.
4. **Error:** something unexpected went wrong and the UI doesn't provide a solution.
5. **Disabled:** nothing is logged

### Examples

* You couldn't check because the server is unavailable: The UI can show the options → *Warning*
* You can't check because the document can't be parsed → *Error*

## UI Options / Defaults

Consider for integrations:

* **Info** is the default logging mode. Typically, an integration doesn't have a UI configuration to change the log level.
* The path of the logging directory should be shown in the start page.
* A button is provided to navigate to the directory using a file explorer.
* (It could be possible to switch logging mode in the registry or a configuration file.)

## Log Format

Each line should contain one log entry. Each log entry should have the following structure:

```text
    <ISO-DATE-WITH-TIME> | [<LOG-LEVEL>] <CLASS-OR-MODULE>: <MESSAGE>
```

### Example

```text
    2016-05-09 15:02:47,226 | [DEBUG] Log4JHandler: configured logging
```

Optionally `<CLASS-OR-MODULE>` could also contain the method name and/or line number.

## Path and Filename

Log files should be written to:

### Mac

```bash
/Users/<USERNAME>/Library/Logs/Acrolinx/APPLICATIONNAME/ISODATE-INTEGRATIONNAME.INSTANCEID.log
```

### Windows

```batch
%TEMP%\Acrolinx\Logs\APPLICATIONNAME\ISODATE-INTEGRATIONNAME.INSTANCEID.log
```

### Linux

```bash
/tmp/acrolinx/logs/APPLICATIONNAME/ISODATE-INTEGRATIONNAME.INSTANCEID.log
```

In this pattern `APPLICATIONNAME` is the host application name,
`ISODATE` is a date in the format `2016-04-30`, and `INTEGRATIONNAME` is the name of the integration.
If another process locks the log file without an ID (`ISODATE-INTEGRATIONNAME.log`),
then `INSTANCEID` is used to resolve the conflict.

## Sensitive Data

Sensitive data is any data related to a person, any credentials. In
Acrolinx programs, the checked contents must also be considered
sensitive, particularly when combined with user-data.

Examples:

* Usernames
* IP-addresses, port numbers, process IDs
* Context of a finding
* Surfaces of terms
* Passwords
* Authentication tokens or session IDs if they act as a hard to guess, shared secret
* File-system paths
* SQL queries with values
* To a certain degree, also stack-traces should be considered
  sensitive as they tell something about how things work.

Please use the following guides to decide what data to log at which levels.

### Error

Errors are rare, exceptional situations. These will usually not show
up in log files. When they do, it may be hard to find out what
happened. Therefore, information like IP-addresses and usernames can
be logged. For example, when you can't reach an Acrolinx URL.

### Warn

Warnings can appear from time to time and aren't critical for the
general function of the program. They can appear in day-to-day
logs. Thus, warning must never contain any sensitive data.

### Info

Logs at Info level happen all the time.  Never log any sensitive data
here.

* Log the ID of users instead of their names.
* Suppress stack-traces

### Debug

The debug level isn't enabled on production systems and only turned
on when an analysis is required. Therefore, almost all sensitive data
can be logged here.

Don't log credentials and other secrets here.

### Trace

Trace is the final frontier. When analyzing an unusual situation, you
expect to find as much information as you can. On this level, it's
allowed to log complete objects and decrypted traffic that went over
the wire encrypted like HTTPS requests.  No special care must be taken
to protect credentials or other secrets here.
