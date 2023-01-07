Data passed through is copied and not shared via reference, the page and worker do not share the same instance.
Data is serialized as it's passed through and then deserialized.


###### Example - Advanced passing JSON and creating switching system
For passing complex data and using different functions on both the main page and worker.

QueryableWorker:
	Takes URL of worker, default listener and an error handler.
	Keeps track of all the listeners and manages communication with the worker.
```js
function QueryableWorker(url, defualtListener, onError) {
	const instance = this;
	const worker = new Worker(url);
	const listeners = {};

	this.defaultListener = defaultListener ?? (() => {});

	if (onError) {
		worker.onerror = onError;
	}

	this.postMessage = (message) => {
		worker.postMessage(message);
	}

	this.terminate = () => {
		worker.terminate();
	}

	this.addListeners = (name, listener) => {
		listeners[name] = listener;
	}

	this.removeListener = (name) => {
		delete listeners[name];	
	}

	/**
		Takes at least one argument, the method name to query.
		Can also pass through any arguments that it should require.
	*/
	this.sendQuery = (queryMethod, ...queryMethodArguments) => {
		if (!queryMethod) {
			throw new TypeError("At least one argument required")
		}

		worker.postMessage({
			queryMethod,
			queryMethodArguments
		})
	}

	worker.onmessage = (event) => {
		if (
			event.data instanceof Object &&
			Object.hasOwn(event.data, "queryMethodListener") &&
			Object.hasOwn(event.data, "queryMethodArguments")
		) {
			listeners[event.data.queryMethodListener].apply(
				instance,
				event.data.queryMethodArguments
			);
		} else {
			this.defaultListener.call(instance, event.data);
		}
	};
}
```

The actual worker script:
```js
	/**
		List of functions that the QueryableWorker is able to query
	*/
	const queryableFunctions = {
		function1() {
			reply("Some info")
		};
		function2() {};
	}

	// Generic system functions
	function defaultReply (message) {
		/**
			default PUBLIC function that will be executed when 
			queryableWorker.postMessage() is called directly
		*/
	}

	function reply (queryMethodListener, ...queryMethodArguments) {
		if (!queryMethodListener)
			throw new TypeError("not enough arguments");

		postMessage({
			queryMethodListener,
			queryMethodArguments
		})
	}

	onmessage = (event) => 
		if (
			event.data instanceof Object &&
			Object.hasOwn(event.data, "queryMethod") &&
			Object.hasOwn(event.data, "queryMethodArguments")
		) {
			queryableFunctions[event.data.queryMethod].apply(
				self,
				event.data.queryMethodArguments
			)
		} else {
			defaultReply(event.data);
		}
	}
```


###### Passing data by transfering ownership (transferable objects)
Transferable objects are transferred from one context to another with a zero-copy operation.
Example:
	If transferring an ArrayBuffer from main app to worker, the original one is cleared and no longer usable.




Fibonacci Example
```js
  let a = 1;
  let b = 0;
  while (num >= 0){
    [a, b] = [a + b, a];
    num--;
  }

  self.postMessage(b);
```