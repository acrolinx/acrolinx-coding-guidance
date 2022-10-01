# Authentication and Setting the Acrolinx URL

## Acrolinx URL

Usually, one of the Acrolinx Sidebar SDKs will cover setting the Acrolinx URL.
Some scenarios might call for prepopulating the Acrolinx URL in different ways:

1. CMS administrator sets the Acrolinx URL for all users.

   Make sure the Acrolinx URL is validated properly.
   To validate an Acrolinx Platform, check if `<SERVER:PORT>/sidebar/v14/index.html`
   is present and contains a `meta` with the name `sidebar-version` like: `<meta name="sidebar-version" content="14.5.0">`.
   Each Acrolinx Platform version has a different Sidebar version.

2. Integration is customer-built and only for your company: you can hard-code the Acrolinx URL.

3. A web server delivers the integration. The web server also acts as a proxy to the Acrolinx Platform.
   You can use a relative Acrolinx URL and set the value on the server side.

4. A software distribution system rolls out the integration.
   The roll-out mechanism might set the Acrolinx URL.

## Authentication

By default, authentication takes place in the Sidebar. The Sidebar opens a web browser page for sign-in.
If users are already authenticated in a CMS, then you ideally use Acrolinx single sign-on (SSO). See points 4 and 5.
The Sidebar and Acrolinx Platform allow different possible configurations:

1. The build-in **Acrolinx authentication** is used with an embedded user database.
   User configuration will be done in the Acrolinx Dashboard.
   The Sidebar will open a browser window where the user signs in to Acrolinx.
   Just configuration on the Acrolinx Platform side is required: no coding effort on the integration side required.
   If Acrolinx traffic is tunneled through a
   [reverse proxy](https://en.wikipedia.org/wiki/Reverse_proxy) and provided as a sub path like:
   `https://myserver/acrolinx/proxy/`, this option can't be used.
   When the Acrolinx services are provided on the top level, then a reverse proxy can be used like: `https://myserver/`.

2. The Acrolinx Platform uses an **External Authentication** like LDAP.
   The user experience will be the same as in 1., but the users aren't configured in the Acrolinx Dashboard.
   Instead the users will be configured on the **LDAP-Server**.
   Just configuration on the Acrolinx Platform side is required: no coding effort on the integration side required.

3. The Acrolinx Platform uses a **Federate Authentication**.
   The user experience will be similar to one, as well as two.
   Instead of signing in at the Acrolinx Platform the user will see a Sign-in page of a **3rd-party system**.
   This option can also be used when traffic is tunneled through a reverse proxy.
   Just a configuration on the Acrolinx Platform side is required: no coding effort on the integration side required.

4. The communication is tunneled through an [Acrolinx single sign-on reverse proxy (SSO)](https://github.com/acrolinx/acrolinx-proxy-sample)
   using, and a shared secret. The user is already authenticated in a CMS.
   A proxy build into the CMS system knows the username of the current session.
   The Acrolinx Platform and the CMS share a secret. The Acrolinx Platform trusts all requests sent with this secret.
   Prevent the Acrolinx Integration of having access to the secret.
   This option is currently only available in JavaScript-based integrations.

5. In embedded integration, the same approach as in 4 can be used.
   Instead of tunneling all traffic through a proxy the secret can be used directly.
   Since no user will have access to the token on the embedded integration, this will be secure as well.

6. In automated integrations sometimes it makes sense to use an **API token** created via the Acrolinx dashboard.
   In that case you'll don't get proper user assignment and analytics might not work as expected.
   You might have to talk to your CSM, if this kind of usage is covered by your license.

Make sure that no hard-coded username is used for checks from different users.

Often the used authentication influences the preferred [check type](check-types.md). See: [integration points](integration-points.md)
