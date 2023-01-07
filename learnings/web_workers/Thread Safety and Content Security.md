
###### Thread Safety
`Worker` interface spawns real OS-level threads.
Due to controller communication points, it is very hard to cause concurrency problems.

###### Content Security Policy
In general they are not governed by the CSP of the document or the the parent worker that created them.

If a document has the following header:
`Content-Security-Policy: script-src 'self'`
It will not be able to use things like `eval()` but a worker spawned from the document will be able to use `eval()`

To add CSP to the worker, set it for the response header of the request that delivered the worker script itself. Conversly if the scripts origin is a glbally unique id, the worker does inherit the documents/parent worker CSP