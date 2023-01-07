##### 1. Multiple String Check
```js
const isVowel = (letter) => 
	['a', 'e', 'i', 'o', 'u'].includes(letter);
```

##### 2. for-of and for-in
```js
// FOR OF
for (const el of array) {
	...
}

// FOR IN
for (const key in object) {
	const value = object[key]
}
```

##### 3. Falsey Checks
Just throw a ! in front.
Checks for null, undefined, 0, false, NaN, "" all at once

##### 4. Ternary
```js
const result = momGay ? "Ha gay" : "Memed"
```

##### 5. Ternary Functions
```js
function f1() {}
function f2() {}

(condition ? f1 : f2) ()
```
NOTE: The call signature of the functions needs to be the same, could risk errors if not.

##### 6. Switch
```js
const days = {
	0: "Sunday",
	1: "Monday",
	2: "Tuesday",
	3: "Wednesday",
	4: "Thursday",
	5: "Friday",
	6: "Saturday",
}
```

##### 7. Fallback values
```js
const name = user?.name || "Name not found"
```