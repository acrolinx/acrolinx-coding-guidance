# Security and safety

## Safety

* Acrolinx Integrations shouldn't cause the host application to crash.
* Ensure that you correctly implement:
    + multithreading and dispatching.
    + memory management. Do you use Automatic Reference Counting (ARC)?

## Security

Make sure that you avoid typical security issues like the [OWASP Top Ten](https://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project).

For example, avoid:

* Storing passwords.
* Logging [sensitive data](logging.md#sensitive-data).
* Injection or cross-site scripting
    + Specifically, be careful inserting suggestions into HTML content when replacing text.
* SSL and TLS
    + If you connect to a secure server, validate the certificate.
      If the connection fails, don't fall back to insecure connections.
      Example: if a user specifies `https://acrolinx.com`, don't automatically try `http://acrolinx.com`.
    + Don't change the VM or system security settings to a less secure setting.
      For example, don't use code to set Java VM settings like this: `https.protocols=TLSv1`.
      If you require such a setting, clearly document and communicate it.
      The customer is then responsible to know this when preparing the rollout.
      *Consider plain TLSv1 and TLSv1.1 as potentially insecure.*


* If you use an [SSO reverse proxy](https://github.com/acrolinx/acrolinx-proxy-sample) for authentication, make sure that:
    + The proxy layer checks the entire authentication.
    + The system that you integrate with already authenticated the username.
    + The proxy adds the username header and the SSO token header.
    + You keep the SSO token secret between the system's backend and Acrolinx.
    + It's impossible to fake a request to the proxy and obtain an authentication token for a user other
      than the authenticated user.
* A URL, that a user might enter, starts with `https?://`.
  Otherwise, it could execute malicious programs.
  An open URL method often maps internally to `ShellExecute` and allows a remote code execution (RCE) attack.

### TLS

Acrolinx instances have the latest security standards.
Standard and HTTP clients might not be able to connect.
Make sure that you configure your VM, operating system, and backend to allow connections with modern TLS versions.

A helpful links:

* Windows or .NET: [How to enable TLS 1.2 on clients](https://docs.microsoft.com/en-us/mem/configmgr/core/plan-design/security/enable-tls-1-2-client)
