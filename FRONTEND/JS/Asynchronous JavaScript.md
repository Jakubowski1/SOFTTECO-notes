#### JavaScript Callbacks

In simple words you are calling a function by another function by passing a function in args.

```js
function myDisplayer(some) {  
  document.getElementById("demo").innerHTML = some;  
}  
  
function myCalculator(num1, num2, myCallback) {  
  let sum = num1 + num2;  
  myCallback(sum);  
}  
  
myCalculator(5, 5, myDisplayer);
```

In the example above, `myDisplayer` is a called a **callback function**.

It is passed to `myCalculator()` as an **argument**.

#### Waiting for a Timeout

```js
setTimeout(myFunction, 3000);  
  
function myFunction() {  
  document.getElementById("demo").innerHTML = "I love You !!";  
}
```

3000 is the number of milliseconds before time-out, so `myFunction()` will be called after 3 seconds.
#### Waiting for Intervals

```js
setInterval(myFunction, 1000);  
  
function myFunction() {  
  let d = new Date();  
  document.getElementById("demo").innerHTML=  
  d.getHours() + ":" +  
  d.getMinutes() + ":" +  
  d.getSeconds();  
}
```

In the example above, `myFunction` is used as a callback.

`myFunction` is passed to `setInterval()` as an argument.

1000 is the number of milliseconds between intervals, so `myFunction()` will be called every second.

#### JavaScript Promise Object

```js
let myPromise = new Promise(function(myResolve, myReject) {  
// "Producing Code" (May take some time)  
  
  myResolve(); // when successful  
  myReject();  // when error  
});  
  
// "Consuming Code" (Must wait for a fulfilled Promise)  
myPromise.then(  
  function(value) { /* code if successful */ },  
  function(error) { /* code if some error */ }  
);
```

| myPromise.state | myPromise.result |
| --------------- | ---------------- |
| "pending"       | undefined        |
| "fulfilled"     | a result value   |
| "rejected"      | an error object  |
Let me break it down in my own words a lil bit

```js
myPromise.then(  
  function(value) { /* code if successful */ },  
  function(error) { /* code if some error */ }  
);
```

The word `then(callbackf1, callbackf2)` takes two arguments for two callbacks in case of success and failure. 

#### Exemplary usage

```js
function myDisplayer(some) {  
  document.getElementById("demo").innerHTML = some;  
}  
  
let myPromise = new Promise(function(myResolve, myReject) {  
  let x = 0;  
  
// The producing code (this may take some time)  
  
  if (x == 0) {  
    myResolve("OK");  
  } else {  
    myReject("Error");  
  }  
});  
  
myPromise.then(  
  function(value) {myDisplayer(value);},  
  function(error) {myDisplayer(error);}  
);
```

Here for example the code waits for a file using Callback:

```js
function getFile(myCallback) {  
  let req = new XMLHttpRequest();  
  req.open('GET', "mycar.html");  
  req.onload = function() {  
    if (req.status == 200) {  
      myCallback(req.responseText);  
    } else {  
      myCallback("Error: " + req.status);  
    }  
  }  
  req.send();  
}  
  
getFile(myDisplayer);
```

And here using promise:

```js
let myPromise = new Promise(function(myResolve, myReject) {  
  let req = new XMLHttpRequest();  
  req.open('GET', "mycar.html");  
  req.onload = function() {  
    if (req.status == 200) {  
      myResolve(req.response);  
    } else {  
      myReject("File not Found");  
    }  
  };  
  req.send();  
});  
  
myPromise.then(  
  function(value) {myDisplayer(value);},  
  function(error) {myDisplayer(error);}  
);
```

### Async 

The keyword `async` before a function makes the function return a promise
```js
async function myFunction() {  
  return "Hello";  
}

Is the same as:

function myFunction() {  
  return Promise.resolve("Hello");  
}
```

And below is the proper usage

```js
async function myFunction() {  
  return "Hello";  
}  
myFunction().then(  
  function(value) {myDisplayer(value);},  
  function(error) {myDisplayer(error);}  
);
```

But for example if you do not expect a bad response

```js
async function myFunction() {  
  return "Hello";  
}  
myFunction().then(  
  function(value) {myDisplayer(value);}  
);
```

### `await`

The `await` keyword can only be used inside an `async` function.

Cool but why do I need that? I checked it and without await this code does not work

```js
        async function myDisplay() {
            let myPromise = new Promise(function(resolve) {
				setTimeout(function() {resolve("I love You !!");}, 3000);
            });
            document.getElementById("count").innerHTML = await myPromise;
        }
myDisplay();
```