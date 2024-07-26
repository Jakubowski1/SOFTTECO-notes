The `try` statement defines a code block to run (to try).

The `catch` statement defines a code block to handle any error.

```js
try {  
  Block of code to try  
}  
catch(_err_) {  
  Block of code to handle errors  
}
```

The `finally` statement defines a code block to run regardless of the result.

```js
try {  
  _Block of code to try  
_}  
catch(_err_) {  
  _Block of code to handle errors  
_}  
finally {  
  _Block of code to be executed regardless of the try / catch result  
_}
```

The `throw` statement defines a custom error.

```js
<p>Please input a number between 5 and 10:</p>  
  
<input id="demo" type="text">  
<button type="button" onclick="myFunction()">Test Input</button>  
<p id="message"></p>  
  
<script>  
function myFunction() {  
  const message = document.getElementById("message");  
  message.innerHTML = "";  
  let x = document.getElementById("demo").value;  
  try {  
    if(x == "") throw "is Empty";  
    if(isNaN(x)) throw "not a number";  
    if(x > 10) throw "too high";  
    if(x < 5) throw "too low";  
  }  
  catch(err) {  
    message.innerHTML = "Input " + err;  
  }  
}  
</script>
```
