Only accessible from the script that called it.

`window.Worker`
	Check if browser supports Web Workers

`const worker = new Worker(*jsfile*)`
	Constructor

`worker.postMessage(*data*)`
	Send message to the worker.
	In the worker file the event handler `onmessage` receives and does any work

`worker.onmessage`
	Event to listen for messages from the worker

`worker.terminate()`
	Terminate running worker immediatly on main thread

Workers can make more workers. Must be hosted within the same origin as the parent page.

`importScripts()`
	- Can accept 0 or many URI's of resources to import.
	- The browser loads each listed script and executes it.
	- Global objects from each script can be used by the worker.
	- `NETWORK_ERROR` is thrown if a script can't be loaded, subsequent code will not be executed.


###### Error Handling
`onerror`
	Called when a runtime error happens.
	Receives `error` named event implementing `ErrorEvent` interface.

Contains 3 main fields of interest:
1. `message` -- Human readable error message
2. `filename` -- Name of script file the error occured
3. `lineno` -- Line the error occured

