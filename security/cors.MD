# Cross-origin resource sharing

* Based on `The Access-Control-Allow-Origin`  header, browsers can discard responses from server if the client is not allowed to read them.
* Only protect the "read" via browsers, but it is not protection against sending request to servers (only responses are not send back to browsers) or
  sending requests via other tool than the browser
* Because of the previous point it can not be used as prevention to CSRF attack.
* Can prevent read data via malicious site, but can not prevent sending requests to server and executing them.
