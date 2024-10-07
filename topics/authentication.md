# Authentication and setting the Acrolinx URL

## Acrolinx URL

The Acrolinx Sidebar SDKs usually handle the Acrolinx URL setting.
Some scenarios might require an admin to set the Acrolinx URL for all users:

1. CMS administrator sets the Acrolinx URL for all users.

   - Make sure that you properly validate the Acrolinx URL.
   - To validate an Acrolinx URL, check if you can connect an integration to an Acrolinx instance.

2. You're a customer and you're building an integration only for your company's use.
   You can hard-code the Acrolinx URL.

3. A web server delivers the integration.
   - The web server also acts as a proxy to Acrolinx.
   - Use a relative Acrolinx URL and set the value on the server side.

4. You use a software distribution system to roll out the integration.
   You can set the Acrolinx URL with the roll-out mechanism.

## Authentication

By default, authentication takes place in the Sidebar. The Sidebar opens a web browser page for sign-in.
If users are already authenticated in a CMS, then you ideally use Acrolinx single sign-on (SSO). See points 4 and 5.
The Sidebar and Acrolinx platform support different authentication options:

1. **Acrolinx Authentication** works with a user database on the Acrolinx platform.
   - Create and manage users in Acrolinx.
   - The Sidebar opens a browser window where users sign in.
   - This option only requires managing users in Acrolinx. You don't have to do any coding in the integration.
   - You cannot use this option if Acrolinx traffic is tunneled through a
   [reverse proxy](https://en.wikipedia.org/wiki/Reverse_proxy) and provided as a subpath like
   `https://myserver/acrolinx/proxy/`
   - If the Acrolinx services are provided on the top-level domain name, then you can use a reverse proxy like `https://myserver/`.

2. Acrolinx uses **external euthentication** like LDAP (Lightweight Directory Access Protocol) or Active Directory.
   - The sign-in user experience is the same as in option 1, but you don't configure users in Acrolinx.
   - Instead, you configure users on the **LDAP-Server**.
   - This option only requires configuration to the external directory on the Acrolinx platform.
   - You don't have to do any coding in the integration.

3. The Acrolinx Platform uses **Enterprise Federated Authentication**.
   - The user experience will be similar to option 1 and 2.
   - Instead of signing in to the Acrolinx Platform, the user will see a Sign-in page of a **3rd-party system**.
   - You can also use this option when traffic is tunneled through a reverse proxy.
   - This option only requires configuration to the external directory on the Acrolinx Platform.
   - You don't have to do any coding in the integration.

4. Communication is tunneled through an [Acrolinx single sign-on (SSO) reverse proxy](https://github.com/acrolinx/acrolinx-proxy-sample)
   using a shared secret.
   - The user is already authenticated in a CMS.
   - A proxy built into the CMS knows the username of the current session.
   - Acrolinx and the CMS share a secret. Acrolinx trusts all requests sent with this secret.
   - For security reasons, prevent Acrolinx from having access to the secret.
   - This option is currently only available for JavaScript-based integrations.

5. For embedded integrations, you can use the same approach as in option 4.
   - You can use the secret directly instead of tunneling all traffic through a proxy.
   - This method is secure since users won't have access to the token of the embedded integration.

6. For automated integrations, you might want to use an **API token**.
   - To create an API token, go to the Settings of the relevant user.
   - All checks will be associated with the user whose API token you're using.
   - Some parts of Analytics dashboards that show usernames might not work as expected.
   - Consult with your CSM or account manager to confirm whether your license includes this kind of usage.

Do not hard-code any usernames for checks run by different users.

The authentication method you use often influences the recommended [check type](check-types.md). See [checking features](checking-features.md).
