# Logging

It's up to you to decide what kind of log messages to create. But if the application crashes or something else goes wrong,
your integration must write log messages. These log messages must include information that helps Acrolinx Support
troubleshoot problems.

## Log at the Correct Level

Log levels:

1. **Trace, Extended, and Debug:** entering an important method

    **Define which Events to Log**

    * `check`
    * `showOptions`
    * `selectRange`
    * `replaceRange`
    * `documentOpened`
    * `documentClosed`
    * `activeDocumentChanged` (not `textChange`)
2. **Normal and Info:** checking or application start or exit
3. **Warning:** something went wrong but the program can handle it. User can resolve the issue in the UI.
4. **Error:** something unexpected went wrong and the UI doesn't provide a solution.
5. **Disabled:** doesn’t log anything.

### Examples

You can't check because:

* The Acrolinx Platform is unavailable: Show the Sidebar **Options** tab → *Warning*
* Acrolinx can't parse your document. → *Error*

## Default Logging

Consider for integrations:

* **Info** is the default logging level. Integrations don't usually have a UI option to change the log level.
* The path of the logging directory appears in the Sidebar start page.
* Users can click a button to navigate to the logging directory in a file explorer.
* (Make it easy for users to enable logging in the registry or a configuration file.)

## Log Format

Each line consists of one log entry. Use the following structure for log entries:

```text
    <ISO-DATE-WITH-TIME> | [<LOG-LEVEL>] <CLASS-OR-MODULE>: <MESSAGE>
```

### Include Pertinent Details

Just enough context:

```text
    2016-05-09 15:02:47,226 | [DEBUG] Log4JHandler: configured logging
```

You can also include the method name, line number, or both in the `<CLASS-OR-MODULE>`.

## File Name and Path

Store log files in the following locations:

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

* `APPLICATIONNAME` is the host name of your application
* `ISODATE` is a YYYY-MM-DD format of `2016-04-30`
* `INTEGRATIONNAME` is the name of the integration

If another process locks the log file without an ID (`ISODATE-INTEGRATIONNAME.log`), use `INSTANCEID` to resolve the conflict.

## Exclude Sensitive Information

Keep security and compliance requirements in mind:

* Don't emit sensitive Personal Identifiable Information (PII).
* Don't emit any credentials or secrets to your logs.
* Remember that any content that Acrolinx checks is also considered sensitive information, particularly when combined
  with user information.

Examples of sensitive information:

* Usernames
* IP addresses, port numbers, process IDs
* Context of a finding
* Surfaces of terms
* Passwords
* Authentication tokens or session IDs if they act as a hard-to-guess, shared secret
* File system paths
* SQL queries with values
* To a certain degree, also stack traces since they reveal how things work.

Use the following guide to decide what information to log at which level.

### Error

Errors are rare, exceptional situations. These will usually not show
up in log files. When they do, it may be hard to find out what
happened. So, you can log information like IP addresses
and usernames. For example, when you can't connect to an Acrolinx URL.

### Warn

Warnings appear from time to time and aren't critical for the
general function of the program. They appear in routine logs.
Therefore, warnings must never contain sensitive information.

### Info

Logs at Info level happen all the time.  Never log any sensitive information
at this level.

* Log the ID of users instead of their names
* Suppress stack traces

### Debug

Customers will not enable the debug level in production. Acrolinx Support might ask
customers to enable it to analyze an issue. You can safely log most sensitive information
at the Debug level.

Don't log credentials and other secrets at the Debug level.

### Trace

Trace is the final frontier. The Trace log level is useful for analyzing
unusual scenarios. Its purpose is diagnostic. Include as much information
as possible. You can even log complete objects and decrypted traffic like HTTPS requests
that went over the wire encrypted. You don't have to hide credentials or other secrets.
