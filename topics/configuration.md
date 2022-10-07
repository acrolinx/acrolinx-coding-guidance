# Authentication and Setting the Acrolinx URL

## Acrolinx URL

The Acrolinx Sidebar SDKs usually handle the Acrolinx URL setting.
Some scenarios might require an admin to set the Acrolinx URL for all users:

1. CMS administrator sets the Acrolinx URL for all users.

   Make sure that you properly validate the Acrolinx URL.
   To validate an Acrolinx Platform URL, check if `<SERVER:PORT>/sidebar/v14/index.html`
   is present and contains a `meta` tag with the name `sidebar-version` like: `<meta name="sidebar-version" content="14.5.0">`.
   Each Acrolinx Platform version has a different Sidebar version.

2. You're a customer and you build an integration only for your company's use.
   You can hard-code the Acrolinx URL.

3. A web server delivers the integration. The web server also acts as a proxy to the Acrolinx Platform.
   Use a relative Acrolinx URL and set the value on the server side.

4. You use a software distribution system to roll out the integration.
   You can set the Acrolinx URL with the roll-out mechanism.

## Authentication

By default, authentication takes place in the Sidebar. The Sidebar opens a web browser page for sign-in.
If users are already authenticated in a CMS, then you ideally use Acrolinx single sign-on (SSO). See points 4 and 5.
The Sidebar and Acrolinx Platform support different authentication options:

1. **Acrolinx authentication** works with a user database on the Acrolinx Platform.
   You can create and manage users in the Acrolinx Dashboard.
   The Sidebar opens a browser window where the user signs in to Acrolinx.
   This option only requires configuration on the Acrolinx Platform. You don't have to do any coding in the integration.
   You cannot use this option if Acrolinx traffic is tunneled through a
   [reverse proxy](https://en.wikipedia.org/wiki/Reverse_proxy) and provided as a subpath like
   `https://myserver/acrolinx/proxy/`
   If the Acrolinx services are provided on the top level, then you can use a reverse proxy like `https://myserver/`.

2. The Acrolinx Platform uses **External Authentication** like LDAP.
   The user experience will be the same as in 1., but the users aren't configured in the Acrolinx Dashboard.
   Instead the users will be configured on the **LDAP-Server**.
   Just configuration on the Acrolinx Platform side is required: no coding effort on the integration side required.

3. The Acrolinx Platform uses **Federated Authentication**.
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
