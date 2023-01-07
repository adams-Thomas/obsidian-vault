
Created by calling a constructor (e.g `worker()`) that then runs a JS file.
Works in another global context from current `window`.
Using `window` instead of `self` to get global scope within a worker will result in an error.

Represented by 
	`DedicatedWorkerGlobalScope` -- Only accessible from parent script
	`SharedWorkerGlobalScope` -- Accessible from other scripts

Can mostly run whatever code you want. [Available functions/classes](https://developer.mozilla.org/en-US/docs/Web/API/Web_Workers_API/Functions_and_classes_available_to_workers)
Exceptions:
 - DOM Manipulation
 - Some `window` default methods and properties

Data is sent between worker and main system using a system of messages.
Messages are sent with `postMessage()` and `onmessage` event handler is used to respond to messages.