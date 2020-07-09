# Websockets

* persistent connection between client and server
* WebSockets provide a bidirectional, full-duplex communications channel over a single TCP/IP socket connection
* can be used to eastablish real-time communication between client and server
* messages are guaranted to arrive in order they were sent, due to TCP and having only one connection

WebSockets begin life as a standard HTTP request and response. Within that request response chain,
the client asks to open a WebSocket connection, and the server responds (if its able to).

WebSockets do not use the `http://` or `https://` scheme (because they do not follow the HTTP protocol). Rather, WebSocket URIs use a new scheme `ws:`
(or `wss:` for a secure WebSocket). The remainder of the URI is the same as an HTTP URI: a host, port, path and any query parameters.

WebSocket connections are established by upgrading an HTTP request/response pair. A client that supports WebSockets and wants to establish
a connection will send an HTTP request that includes a few required headers:

* `Connection: Upgrade`
* `Upgrade: websocket`
* `Sec-WebSocket-Key`
* `Sec-WebSocket-Version`

# Long polling
* Alternative or fallback way for implementing real-time behavior when websocket is not supported
* The client send HTTP request with a long timeout and the server do not respond to that request until some desired event occurs. When the connection timeouts
  the client send new request with long timeout and so on.
* Resources on the server are being used, even when no data is available to send.
* Responses are not guaranteed to come in same order if multiple connections are opened at the same time.
  
# Periodic polling
* The client ask server for data every `n` seconds/minutes/whatever. Not really realtime and result in more requests that "long polling".

* TODO: authentication and security
