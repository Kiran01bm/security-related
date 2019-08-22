## Notes
OIDC and SAML are popular choices for SSO.
1. OIDC - JSON and Web Friendly, For REST - OIDC and then SAML
2. SAML - XML and SOAP Friendly, For SOAP - SAML

## Background
1. [OpenID Connect](http://openid.net/connect/) (OIDC) is an authentication protocol that is an extension of OAuth 2.0.
 
2. While [OAuth 2.0](https://tools.ietf.org/html/rfc6749) is only a framework for building authorization protocols and is mainly incomplete, OIDC is a full-fledged authentication and authorization protocol. OIDC also makes heavy use of the [Json Web Token](https://jwt.io/) (JWT) set of standards.
 
3. There are really two types of use cases when using OIDC.
 
4. OIDC has **4 different ways for a client or application to authenticate a user and receive an identity and access token.** Which path you use depends greatly on the type of application or client requesting access.
```
1. Authorization Code Flow - Comprehensive
2. Implicit Flow - Cut down version of Authorization code flow.
3. Direct Access Grant - Input is User Credentials (uid and upwd) + Client Credentials (clientId and clientSecret).
4. Client Credentials Grant - Input is only Client Credentials (clientId and clientSecret).
```
5. Clients are entities that can request authentication of a user from a Single SignOn Server. Clients come in two forms. Note: Each OIDC client has a built in service account which allows it to obtain an access token.
```
1. The first type of client is an application that wants to participate in single-sign-on. These clients just want Single Sign-On to provide security for them. I call it ** Server side Client **
2. The other type of client is one that is requesting an access token so that it can invoke other services on behalf of the authenticated user. I call it ** Client side Client **

confidential
Confidential access type is for server-side clients that need to perform a browser login and require a client secret when they turn an access code into an access token, (see Access Token Request in the OAuth 2.0 spec for more details). This type should be used for server-side applications.

public
Public access type is for client-side clients that need to perform a browser login. With a client-side application there is no way to keep a secret safe. Instead it is very important to restrict access by configuring correct redirect URIs for the client.

bearer-only
Bearer-only access type means that the application only allows bearer token requests. If this is turned on, this application cannot participate in browser logins.
```


## Info about SAML
SAML 2.0 is a similar specification to OIDC but a lot older and more mature. It has its roots in SOAP and the plethora of WS-* specifications so it tends to be a bit more verbose than OIDC. SAML 2.0 is primarily an authentication protocol that works by exchanging XML documents between the authentication server and the application.
 
There is really two types of use cases when using SAML:
1. The first is an application that asks the Red Hat Single Sign-On server to authenticate a user for them. After a successful login, the application will receive an XML document that contains something called a SAML assertion that specify various attributes about the user. This XML document is digitally signed by the realm and contains access information (like user role mappings) that the application can use to determine what resources the user is allowed to access on the application.
2. The second type of use cases is that of a client that wants to gain access to remote services. In this case, the client asks Red Hat Single Sign-On to obtain an SAML assertion it can use to invoke on other remote services on behalf of the user.

#### SAML Bindings
There are 3 SAML binding variants - 2 of them for Browser based applications and 1 of them for REST client
```
1. Redirect Binding
2. Post Binding
3. ECP for REST and SOAP based clients
```
