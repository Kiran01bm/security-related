# General Notes

The Cache-Control HTTP/1.1 general-header field is used to specify directives for caching mechanisms in both requests and responses.

Example with curl and dynamic query string to trick the remote and proxies.. 

**Note:** curl doesn't cache anything, it simply sends a HTTP request to the server and then it pipes all data it receives on to 
the write callback that you provide. There's no caching, no middle layers, no magic.
```
curl -I -H 'Cache-Control: no-store' https://colnny.com/play$(date +%s)
```

## No caching
The cache should not store anything about the client request or server response. A request is sent to the server and a full response is downloaded each and every time.

```
Cache-Control: no-store
```

## Cache but revalidate
A cache will send the request to the origin server for validation before releasing a cached copy.
```
Cache-Control: no-cache
```

## Private and public caches

The "public" directive indicates that the response may be cached by any cache. This can be useful if pages with HTTP authentication, or response status codes that aren't normally cacheable, should now be cached.

On the other hand, "private" indicates that the response is intended for a single user only and must not be stored by a shared cache. A private browser cache may store the response in this case.

```
Cache-Control: private
Cache-Control: public
```

## Expiry
The most important directive here is max-age=<seconds>, which is the maximum amount of time in which a resource will be considered fresh. 

This directive is relative to the time of the request, and overrides the Expires header (if set). 

For the files in the application that will not change, you can normally use aggressive caching. This includes static files such as images, CSS files, and JavaScript files, for example.

```
Cache-Control: max-age=31536000
```


## Validation

When using the "must-revalidate" directive, the cache must verify the status of the stale resources before using it and expired ones should not be used. For more details, see the Validation section below.
```
Cache-Control: must-revalidate
```


