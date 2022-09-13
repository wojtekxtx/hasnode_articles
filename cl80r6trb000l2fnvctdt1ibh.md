## Using then() vs Async/Await in JavaScript

When making async requests, you can either use `then()` or `async/await`; both are very similar.
The difference is that in an `async` function, JavaScript will pause the function execution until the promise settles. With `then()`, however, the rest of the function will continue to execute but JavaScript won't execute the `.then()` callback until the promise settles.

Consider the following example:

```javascript
async function test() {
  console.log('Ready');
  let example = await fetch('http://httpbin.org/get');
  console.log('I will print second');
}
test();
console.log('I will print first');
```

If you use promise chaining with `then()`, you need to put any logic you want to execute **after** the request in the promise chain. Any code that you put after `fetch()` will execute immediately, **before** the `fetch()` is done.

```javascript
function test() {
  console.log('Ready');
  let example = fetch('http://httpbin.org/get').then((res) => {
    console.log('This is inside the then() block');
  });
  console.log('This is after the fetch statement where we are now executing other code that is not async');
}

test();
console.log('this is after the entire function');
```

We recommend using async/await where possible, and minimize promise chaining. Async/await makes JavaScript code more accessible to developers that aren't as familiar with JavaScript, and much easier to read.