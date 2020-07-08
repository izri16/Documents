# HTTP

## Versions

### HTTP/1.0
By default every connection was terminated after server response. That could be overriden using `keep-alive` header. When `keep-alive` was supplied server kept
the connection open unless a specific time period has elapsed e.g. 1 minute. Therefore when sending multiple requests it was more efficient as there was no need
to establish the new connection for each request.
Browsers supported only one open connection at a time.

### HTTP/1.1
The `keep-alive` header is being sent by default, unless explicitely set not to.
Browsers allow opening multiple connections (around 4-8), but within one connection only one request can be send at once.

There is concept of *pipelining* which allows browsers to send all requests at once within one connection, but the responses must arrive in the same
order as were the requests sent. If e.g. the first response is slow, all other responses must wait. The issue with *pipelining* is however that it is
not well supported accross browsers and http servers.

### HTTP/2.0
Introduce multiple "performance" updates. Currently supported by most browsers but also http server must be configured for that version (nginx).
* Server push: server can send the resources it believes will be needed for a page to load. E.g. when downloading `index.html` server can also send all `js` and
  `css` files that would otherwise have to be re-requested by the browser after parsing the `index.html`.
* Multiplexed instead of ordered requests: put simply, multiplexing allows your Browser to fire off multiple requests at once on the same connection and receive the requests back in any order.
  This can significantly improve the page load time as the requests are not being blocked by each other and there is also not the overhead of managing multiple
  connections on both the browser and the server side.

Usefull resources:

https://stackoverflow.com/questions/36517829/what-does-multiplexing-mean-in-http-2

https://freecontent.manning.com/animation-http-1-1-vs-http-2-vs-http-2-with-push/
