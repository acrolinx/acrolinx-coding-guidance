# Authentication and Acrolinx URL Configuration

## Acrolinx URL

Typically one of the Acrolinx Sidebar SDK will take care to configure the Acrolinx URL.
In some situations it might make sense that the Acrolinx URL is prepopulated in different ways:

1. A CMS the administrator configures the Acrolinx URL for all users.
   In this case, make sure that the Acrolinx URL is validated properly.
   A good way to validate an Acrolinx Platform is to check if `<SERVER:PORT>/sidebar/v14/index.html`
   is present and contains a `meta` with the name `sidebar-version` like: `<meta name="sidebar-version" content="14.5.0">`.
   Keep in mind that the version differs in each Acrolinx Platform version.
2. The integration is internally developed and only for your company: the Acrolinx URL can be hard-coded.
3. A web server delivers the integration. The web server also acts as proxy to the Acrolinx Platform.
   In this case, a relative Acrolinx URL can be used, and the server configuration is done at server side.
4. A software distribution system rolls out the integration.
   In this case, the Acrolinx URL might be set by the roll-out mechanism.

## Authentication

By default the authentication takes place in the Sidebar. The Sidebar will open a browser page for sign-in, if required.
If users are already authenticated in some CMS context, ideally the Acrolinx single sign-on (SSO) is used. See: 4 and 5.
Different possible configurations can be done with the Sidebar and Acrolinx Platform:

1. The build-in **Acrolinx authentication** is used with an embedded user database.
   User configuration will be done in the Acrolinx Dashboard.
   The Sidebar will open a browser window where the user signs in to Acrolinx.
   Just configuration on Acrolinx Platform side is required: no coding effort on integration side required.
   If Acrolinx traffic is tunneled though a
   [reverse proxy](https://en.wikipedia.org/wiki/Reverse_proxy) and provided as a sub path like:
   `https://myserver/acrolinx/proxy/`, this option can't be used.
   When the Acrolinx services are provided on top level, then a reverse proxy can be used like: `https://myserver/`.
2. The Acrolinx Platform uses an **External Authentication** like LDAP.
   The user experience will be the same as in 1., but the users aren't configured in the Acrolinx Dashboard.
   Instead the users will be configured on the **LDAP-Server**.
   Just configuration on Acrolinx Platform side is required: no coding effort on integration side required.
3. The Acrolinx Platform uses a **Federate Authentication**.
   The user experience will be similar to one, as well as two.
   Instead of signing in at the Acrolinx Platform the user will see a Sign-in page of a **3rd-party system**.
   This option can also be used when traffic is tunneled though a reverse proxy.
   Just configuration on Acrolinx Platform side is required: no coding effort on integration side required.
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
