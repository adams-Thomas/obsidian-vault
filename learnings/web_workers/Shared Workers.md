Accessible by multiple scripts -- even if being accessed by different windows, iframes, workers. 

`window.SharedWorker()`
	Constructor

Only difference between this and [[Dedicated Workers]] is needing to add `.port` after `onmessage` and `postmessage`

Example:
<small>Main Script</small>
```
const worker = new ShareWorker(somefile.hs);
worker.port.postMessage([value1, value2]);
worker.port.onmessage = (event) => {};
```

<small>Worker:</small>
```
onconnect = (e) => {
	const port = e.ports[0];
	port.onmessage = (e) => {}
}
```
<sup>Dedicated worker just needs an `onmessage`</sup>
