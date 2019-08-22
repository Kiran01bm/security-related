## Notes
Authorization Code Flow is a browser-based protocol is the recommended method to  use to authenticate and authorize browser-based applications. It makes **heavy use of browser redirects to obtain an identity and access token**. Here’s a brief summary:

## Flow
1. Browser visits application. The application notices the user is not logged in, so it redirects the browser to Single Sign-On server to be authenticated. The application passes along a callback URL (a redirect URL) as a query parameter in this browser redirect that Single Sign-On server will use when it finishes authentication.
2. Single Sign-On authenticates the user and creates a one-time, very short lived, temporary code. Single Sign-On server redirects back to the application using the callback URL provided earlier and additionally adds the temporary code as a query parameter in the callback URL.
3. The application extracts the temporary code and makes a background out of band REST invocation to Single Sign-On server to exchange the code for an **identity, access and refresh token**. Another important aspect of this flow is the concept of a public vs. a confidential client. Confidential clients are required to provide a **client secret** when they exchange the temporary codes for tokens. Public clients are not required to provide this client secret. Public clients are perfectly fine so long as HTTPS is strictly enforced and you are very strict about what redirect URIs are registered for the client. HTML5/JavaScript clients always have to be public clients because there is no way to transmit the client secret to them in a secure manner. Again, this is ok so long as you use HTTPS and strictly enforce redirect URI registration.

** Security Notes: **

**Once this temporary code has been used once to obtain the tokens, it can never be used again. This prevents potential reply attacks.**

It is important to note that access tokens are usually short lived and often expired after only minutes. The additional refresh token that was transmitted by the login protocol allows the application to obtain a new access token after it expires. This refresh protocol is important in the situation of a compromised system. If access tokens are short lived, the whole system is only vulnerable to a stolen token for the lifetime of the access token. Future refresh token requests will fail if an admin has revoked access. This makes things more secure and more scalable.

## OIDC URI Endpoints ex: Red Hat SSO
Here’s a list of OIDC endpoints that the Red Hat Single Sign-On publishes. These URLs are useful if you are using a non-Red Hat Single Sign-On client adapter to talk OIDC with the auth server. These are all relative URLs and the root of the URL being the HTTP(S) protocol, hostname, and usually path prefixed with /auth: i.e. https://localhost:8080/auth

/realms/{realm-name}/protocol/openid-connect/token
This is the URL endpoint for obtaining a temporary code in the Authorization Code Flow or for obtaining tokens via the Implicit Flow, Direct Grants, or Client Grants.

/realms/{realm-name}/protocol/openid-connect/auth
This is the URL endpoint for the Authorization Code Flow to turn a temporary code into a token.

/realms/{realm-name}/protocol/openid-connect/logout
This is the URL endpoint for performing logouts.

/realms/{realm-name}/protocol/openid-connect/userinfo
This is the URL endpoint for the User Info service described in the OIDC specification.

**Note:** In all of these replace {realm-name} with the name of the realm.
