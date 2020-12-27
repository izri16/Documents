# AJAX
### Asynchronous javascript and xml

In the "old days" browsers had to reload the whole page in order to get any changes.
In the early days messages were send in XML later JSON took the popularity.

First famous AJAX implementation was based on *XMLHttpRequest*.
The modern AJAX implementation nowadays is *fetch* which improved the API and added
support for promises.

### What can fetch do? (that XMLHttpRequest can not)
1. Use browser Cache API
2. Streaming support for responses, except only buffering all in memory

### Current fetch limitations (what XMLHttpRequest can do)
1. client can not abort request
2. client can not get request progress (upload/download)

*Note: there are more differences between the two, but the above I find most relevant.*

Due to current *fetch* limitations it is not yet suitable for all use cases. Axios https://github.com/axios/axios is a nice library that adds Promise
API to *XMLHttpRequest* thus taking the best from both the worlds (unless you need *fetch* functionality that the *XMLHttpRequest* does not have, e.g. when working
with ServiceWorkers and using Cache API)
