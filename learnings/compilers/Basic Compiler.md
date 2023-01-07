Basic compiler example.
Will compile Lisp into Javascript.

Example:
Javascript
```js
add(2, sub (4, 3))
```
Lisp:
```lisp
(add 2 (sub 4 3))
```

The compiler goes through for steps:
1. [[Lexical Analysis]]
2. Syntatctical Analysis
3. Transformation
4. Code Generation

