# General Notes

gRPC uses HTTP/2 which can be compared with websockets. Althuough HTTP/2 is not a replacement for push technologies such as WebSocket or SSE.

HTTP/2 and SSE (Server-Sent Events) provides efficient HTTP-based bidirectional communication.

HTTP/2 is Client Server with Server Push in the background, So you make a request and simply stay on that connection listeneing for updates without having to poll. Essentially you are telling the Server - Let me know when updates happen related to the thing I just did"

![Diff Http2 Websockets](../images/http2websockets.png?raw=true "HTTP2 Websockets")

![HTTP2 Demo](../images/gophertiles.png?raw=true "HTTP2 Demo")
