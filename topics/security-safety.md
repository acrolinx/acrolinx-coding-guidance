# Security and Safety

## Safety

* Acrolinx Integrations must not cause the host application to crash.
* Ensure that:
    + multithreading and dispatching is implemented correctly.
    + memory management implemented correctly. Is Automatic Reference Counting (ARC) used or not?

## Security

Make sure that you avoid typical security issues like the [OWASP Top Ten](https://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project),
for example:

* injection / cross-site scripting
    + Specifically, be careful inserting strings into HTML when doing replacements.
* SSL / TLS
    + If you connect to a secure server,
      validate the certificate and don't fall back to insecure connections if the connection fails.
      Example: if the user specifies `https://acrolinx.com`, don't automatically try `http://acrolinx.com`.
    + Make sure that you don't change the VM or system security settings to a less secure setting.
      For example, don't set Java VM settings like `https.protocols=TLSv1`, by code.
      If such a setting is required, it must be clearly documented and communicated.
      It's then up to the rollout to take care having everything in place.
      *Keep in mind that plain TLSv1 and TLSv1.1 have to be considered as potentially insecure.*
* Don't store passwords.
* Don't log [sensitive data](logging.md#sensitive-data).
* If you use an [SSO reverse proxy](https://github.com/acrolinx/acrolinx-proxy-sample) for authentication, make sure that:
    + The entire authentication is checked in the proxy layer.
    + The username is already authenticated in the system you integrate.
    + The proxy adds the username header and the SSO token header.
    + The SSO token is kept secret between the system's backend and the Acrolinx Platform.
    + It's impossible to fake a request to the proxy and obtain an authentication token for a different user
      than the authenticated user.
* If you open a URL, that potentially can be entered by a user, make sure that it starts with `https?://`.
  Otherwise it might be feasible to execute programs.
  Often an open URL method is internally mapped to `ShellExecute` and allows a remote code execution.

### TLS

The Acrolinx Platform usually runs on state-of-the-art security standards.
Out of the box and HTTP clients might not be able to connect.
Make sure that you configured your VM, operating system, and backend to allow connections with modern TLS versions.

Some helpful links:

* Windows / .NET: [How to enable TLS 1.2 on clients](https://docs.microsoft.com/en-us/mem/configmgr/core/plan-design/security/enable-tls-1-2-client)
* Java: [Java HTTPS Tester](https://github.com/acrolinx/java-https-tester)
