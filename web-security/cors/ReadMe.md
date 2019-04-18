# CORS - Cross-Origin Resource Sharing

## General

Based on [work here](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)

The CORS mechanism supports secure cross-origin requests and data transfers between browsers and web servers. Modern browsers use CORS in an API container such as **XMLHttpRequest** or **Fetch** to help mitigate the risks of cross-origin HTTP requests.

Cross-Origin Resource Sharing (CORS) is a mechanism that uses additional HTTP headers to tell a browser to let a web application running at one origin (domain) have permission to access selected resources from a server at a different origin.

An **example** of a cross-origin request: The frontend JavaScript code for a web application served from http://domain-a.com uses XMLHttpRequest to make a request for http://api.domain-b.com/data.json.

## Scenarios
1. Simple Requests
2. Preflighted Requests
3. Requests with Credentials - (Not covered here)

Unlike “simple requests”, "preflighted" requests first send an HTTP request by the **OPTIONS** method to the resource on the other domain, in order to determine whether the actual request is safe to send. Cross-site requests are preflighted like this since they may have implications to user data.

In particular, a request is preflighted if any of a set of conditions is true, 3 of such conditions is listed below ( there are a few more though ):
	If the request uses any of the following methods:
		PUT
		DELETE
		CONNECT
		OPTIONS
		TRACE
		PATCH
	A customized" (non-standard) HTTP request header being set
	Request uses uses a Content-Type of application/xml

## HTTP Request Headers:

**Origin**
```
Origin: http://foo.example
```

**Access-Control-Request-Method** - Used when issuing a preflight request to let the server know what HTTP method will be used when the actual request is made.

**Access-Control-Request-Headers** - Used when issuing a preflight request to let the server know what HTTP headers will be used when the actual request is made.

## HTTP Response Headers

**Access-Control-Allow-Origin** 

Ex: Allow * - which means that the resource can be accessed by any domain in a cross-site manner.

```
Access-Control-Allow-Origin: *
```

Ex: Allow only specified Origins - No domain other than http://foo.example (identified by the ORIGIN: header in the request) can access the resource in a cross-site manner
```
Access-Control-Allow-Origin: http://foo.example
```
**Access-Control-Allow-Methods** - Specifies the method or methods allowed when accessing the resource.
**Access-Control-Allow-Headers** Indicates which HTTP headers can be used when making the actual request. 
**Access-Control-Max-Age** - Indicates how long the results of a preflight request can be cached.
**Access-Control-Expose-Headers** - Lets a server whitelist headers that browsers are allowed to access.

## Error Handling
CORS failures result in errors, but for security reasons, specifics about what went wrong are not available to JavaScript code. All the code knows is that an error occurred. The only way to determine what specifically went wrong is to look at the browser's console for details.

## Images

### Preflight Flow

Also check the sample JS snippet which triggers a Preflight scenario.

![Preflight Flow](cors_PreFlight.jpg)
