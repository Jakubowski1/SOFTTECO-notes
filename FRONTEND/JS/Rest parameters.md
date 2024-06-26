Allows JS to take in any number of parameters you want
#### Syntax
```js
function f(a, b, ...theArgs) {
  // …
}
```

#### Example 
```js
function sum(...theArgs) {
  let total = 0;
  for (const arg of theArgs) {
    total += arg;
  }
  return total;
}

console.log(sum(1, 2, 3));
// Expected output: 6

console.log(sum(1, 2, 3, 4));
// Expected output: 10
```

==**Remark**==
The parameters are not the array but rest parameters are. This means

```js
function matiSummary(a,b, ...restParameters){
console.log("a", a);
console.log("b", b);
console.log("restParameters", restParameters);
}

matiSummary(4);
// a, "4"
// b, undefined
// restParameters, [] <-- still an array
```

==**Remark2**==
The rest parameters count can be given by length property.
```js
function amount(...args){
console.log(args.length);
}

amount(1,2,3);

//3
```

==**FUN EXERCISE**==
```js
function multiply(multiplier, ...args){
return args.map((element) => element * multiplier);
}

console.log(multiply(2,2,3,10)); //[4,6,20]
```

Here is the short code which shows why normal parameters suck. So as above I now know that rest parameters can behave like an array a little bit. Look here:
```js
function fn(a, b) { 
const normalArray = Array.prototype.slice.call(arguments); //same
const normalArray2 = [].slice.call(arguments); //same
const normalArrayFrom = Array.from(arguments); //same
const first = normalArray.shift(); // OK, gives the first argument const
firstBad = arguments.shift(); // ERROR (arguments is not a normal array) }
```

YOU HAVE TO CONVERT ARGUMENTS TO ARRAY FIRST TO GET THE FIRST ONE. This makes sense because they are unordered. 

The alternative with rest parameters: 
```js
function fn(...args) {
  const normalArray = args; //SEE HERE JUST ASSIGNMENT NO CONVERSION!!!
  const first = normalArray.shift(); // OK, gives the first argument
}
```