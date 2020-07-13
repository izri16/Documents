# CSRF

User is logged to site "Secret-site" using cookies. User visit malicious site which send request to some secured endpoint on "Secret-site". The browser automatically
send the cookies for "Secret-site" so the request will be successfull. Malicious site can e.g. delete some data / send money / whatever.

Options to avoid CSRF:
* Check `Origin` header on server. Modern browsers should not fake it, but in general it is not considered secure.
* When user is authenticated store some csrf token in "localStorage" and send it in header with each request. The malicious site can not access "localStorage".
* When user is authenticated also send csrf cookie and require that cookie to be send in some specific header. The malicious site can send that cookie, but can not
  put it to desired header. Django does csrf protection similar to this.

Use library, do not protect yourself using custom solution!

## websockets
Based on this https://www.christian-schneider.net/CrossSiteWebSocketHijacking.html article it is possible to perform similar attack as is the CSRF. The malicious site can send the request during the handshake/upgrade process phase. It will automatically send the cookies (as ws request is regular http request) and the attacker website can create the connection with ability to read/write data. The CORS protection also does not work for ws or wss protocol.

This can be avoided either by:

Check Origin header on server. Modern browsers should not be able to fake it.
Better: Use similar protection as CSRF does using extra token.
Ideally use some library for that and do not implement the protection on your own.
