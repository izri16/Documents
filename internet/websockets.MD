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

# Security when using with cookie based authentication
Based on this https://www.christian-schneider.net/CrossSiteWebSocketHijacking.html article it is possible to perform similar attack as is the CSRF.
The malicious site can send the request during the handshake/upgrade process phase. It will automatically send the cookies (as `ws` request is regular `http` request) and the attacker website can create the connection with ability to read/write data.
The CORS protection also does not work for `ws` or `wss` protocol.

This can be avoided either by:
* Check `Origin` header on server. Modern browsers should not be able to fake it.
* Better: Use similar protection as CSRF does using extra token.
* According to https://blog.jimmyli.us/articles/2020-08/Cross-Site-WebSocket-Hijacking-With-SocketIO socket.io is not protected to it when using cookies. One can however implement one (or both) of the above checks using custom socket.io middleware. Similar check could be done for Apollo subscriptions.

Ideally use some library for that and do not implement the protection on your own.

# Socket.io
Library that can handle Websocket protocol, but also have fallback options to simulate realtime behavior for old browser or cases when websocket connection fails
(long polling).
* Has built-in reconnect after connection is lost (Websocket does not do that automatically).
* Has built-in broadcast (Websocket does not have that).
* Allows organization of sockets into rooms and namespaces (Websocket does not have that).
* Allows sending JSON data
* Built on Engine.IO
* Can work behing load balancer or nginx

# Apollo subscriptions (graphql)
* Can handle subscription (real-time data) for graphql server
* For Apollo one can choose whatever transport he wants to use (Disclaimer: currently the only stable seems to be pure Websocket transform, there is also socket.io transform which supports long polling but does not seem to be widely used)
* Using only websocket transform (no backdoor for long polling) should work fine for 98% of browsers and should be enough in real-life

# Using multiple servers (nodes)
1. In order to broadcast to all sockets in "room" one must store socket-info in so called "adapter" that all nodes can read from. Adapter stores relation between sockets and rooms. Usually redis using pub/sub model is used, but one call also store socket-info in postgres, firebase, whatever. Storing in memory is fine when using only a single server.
2. To achieve that client always communicates with the same server (important during creation of the socket, as there is an extra "upgrade" phase), one should setup **sticky sessions** using the http proxy, e.g. Nginx.

Sticky sessions can be implemented based on cookie (recommended, or based on some token) or based on ip address of the client.
The above steps also hold true when using "cluster" mode for nodejs.
