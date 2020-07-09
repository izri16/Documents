# THIS is JS

In most cases, the value of `this` is determined by how a function is called (runtime binding).
It can't be set by assignment during execution, and it may be different each time the function is called.
ES5 introduced the `bind()` method to set the value of a function's this regardless of how it's called.
To set the value of `this` to a particular value when calling a function, use `call()`, or `apply()`.

### 1. Outside of function
In the global execution context (outside of any function), `this` refers to the global object whether in strict mode or not.
In the browser it refers to `window` object.

### 2. Calling top level function 
```
function f1() {
  return this;
}

// In a browser and in non "strict" mode
f1() === window; // true

// In "strict" mode `this` would be `undefined`
```
### 3. Constructor function
When creating object via "constructor" function using `new` the `this` inside that function is the object being created by that function.
Same holds for `class` keyword which is just a syntax sugar.

### 4. Arrow functions
In arrow functions, `this` retains the value of the enclosing lexical context's `this`. In global code, it will be set to the global object.

### 5. As an object method
When a function is called as a method of an object, its `this` is set to the object the method is called on.

## globalThis
The `globalThis` property provides a standard way of accessing the global `this` value (and hence the global object itself) across environments. Unlike similar properties such as `window`, it's guaranteed to work in `window` and `non-window` contexts.
