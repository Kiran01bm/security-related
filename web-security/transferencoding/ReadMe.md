## General Notes

Transfer-Encoding is a **hop-by-hop header**, that is applied to a message between two nodes, not to a resource itself. Each segment of a multi-node connection can use different Transfer-Encoding values. 

If you want to compress data over the whole connection, use the end-to-end Content-Encoding header instead.

Ex:
```
// Several values can be listed, separated by a comma
Transfer-Encoding: gzip, chunked
```

### Possible Values:

1. Transfer-Encoding: chunked - HTTP/2 doesn't support HTTP 1.1's chunked transfer encoding mechanism, as it provides its own, more efficient, mechanisms for data streaming.
2. Transfer-Encoding: compress
3. Transfer-Encoding: deflate
4. Transfer-Encoding: gzip
5. Transfer-Encoding: identity
