## Notes

This is a browser-based protocol that is similar to Authorization Code Flow except there are fewer requests and no refresh tokens involved. This flow is **not recommended** as there remains the possibility of access tokens being leaked in the browser history as tokens are transmitted via redirect URIs (see below). Also, **since this flow doesn’t provide the client with a refresh token**, access tokens would either have to be long-lived or users would have to re-authenticate when they expired. This flow is supported because it is in the OIDC and OAuth 2.0 specification. 

Here’s a brief summary of the protocol:

1. Browser visits application. The application notices the user is not logged in, so it redirects the browser to Single Sign-On server to be authenticated. The application passes along a callback URL (a redirect URL) as a query parameter in this browser redirect that Single Sign-On server will use when it finishes authentication.
2. Single Sign-On authenticates the user and creates an **identity and access token**. Single Sign-On server redirects back to the application using the callback URL provided earlier and additionally adding the **identity and access tokens as query parameters in the callback URL.**
3. The application extracts the the identity and access tokens from the callback URL.
