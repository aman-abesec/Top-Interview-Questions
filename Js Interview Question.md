# JavaScript Interview Questions & Answers

## Basic Level

### 1. What is JavaScript and its common uses?

JavaScript is a programming language used to make web pages dynamic and
interactive.

**Common uses:** - DOM manipulation\
- Form validation\
- Backend development (Node.js)\
- Creating APIs\
- Game development

``` js
document.body.style.background = "lightblue";
```

### 2. What are template literals in JavaScript?

Template literals allow embedding variables using backticks `` ` `` with
`${}` syntax.

``` js
let name = "Aman";
console.log(`Hello, ${name}!`);
```

### 3. What is hoisting?

JavaScript moves declarations to the top of the scope before execution.

``` js
console.log(x); // undefined
var x = 10;
```

### 4. Difference between let, var, and const.

  Keyword   Scope      Reassign   Redeclare
  --------- ---------- ---------- -----------
  var       function   ✔          ✔
  let       block      ✔          ✘
  const     block      ✘          ✘

### 5. Data types in JavaScript.

-   Primitive: string, number, boolean, null, undefined, bigint, symbol\
-   Non-primitive: object, array, function

### 6. What is an array, and how to access elements?

``` js
let arr = [10, 20, 30];
console.log(arr[1]); // 20
```

### 7. Difference between == and ===.

``` js
5 == "5"   // true
5 === "5"  // false
```

### 8. Purpose of isNaN()

``` js
isNaN("abc"); // true
isNaN(123);   // false
```

### 9. null vs undefined

  null                      undefined
  ------------------------- ---------------------------
  intentional empty value   declared but not assigned

### 10. typeof operator

``` js
typeof 10;        // "number"
typeof "hello";   // "string"
```

------------------------------------------------------------------------

## Intermediate Level

### 1. map() method

``` js
let nums = [1, 2, 3];
let doubled = nums.map(n => n * 2);
```

### 2. Event bubbling vs capturing

``` js
element.addEventListener("click", handler, true); // capturing
element.addEventListener("click", handler, false); // bubbling
```

### 3. Higher-order functions

``` js
function greet() { console.log("Hi"); }
function wrapper(fn) { fn(); }
wrapper(greet);
```

### 4. IIFE

``` js
(function () {
  console.log("IIFE running...");
})();
```

### 5. Closures

``` js
function counter() {
  let count = 0;
  return function () {
    count++;
    return count;
  };
}
```

### 6. setTimeout & setInterval

``` js
setTimeout(() => console.log("Once"), 1000);
setInterval(() => console.log("Repeat"), 1000);
```

### 7. Promises

``` js
let p = new Promise(resolve => resolve("Done"));
```

### 8. async/await

``` js
async function demo() {
  let result = await fetchData();
}
```

### 9. call, apply, bind

``` js
func.call(obj, a, b);
func.apply(obj, [a, b]);
let newFn = func.bind(obj);
```

### 10. Event delegation

``` js
document.querySelector("ul").addEventListener("click", (e) => {
  if (e.target.tagName === "LI") console.log(e.target.textContent);
});
```

------------------------------------------------------------------------

## Advanced Level

### 1. Event loop

JavaScript handles async operations by executing callback queue tasks
when call stack is empty.

### 2. Promises vs async/await

-   Promises use `.then()`, `.catch()`
-   async/await is cleaner and synchronous-looking

### 3. reduce() method

``` js
[1,2,3].reduce((acc, v) => acc + v, 0);
```

### 4. Currying

``` js
function sum(a) {
  return b => c => a + b + c;
}
```

### 5. Generator functions

``` js
function* gen() {
  yield 1;
  yield 2;
}
```

### 6. WeakMap and WeakSet

-   WeakMap: keys must be objects\
-   WeakSet: stores objects only

### 7. Memory management

Uses garbage collection (mark-and-sweep).

### 8. Shallow vs Deep Copy

``` js
let a = { x: 1 };
let b = Object.assign({}, a);

let deep = JSON.parse(JSON.stringify(a));
```

### 9. Strict mode

``` js
"use strict";
```

### 10. Observer pattern

``` js
class Subject {
  constructor() { this.obs = []; }
  subscribe(fn) { this.obs.push(fn); }
  notify(data) { this.obs.forEach(fn => fn(data)); }
}
```
