There are soo many useful applications for this feature

```js 
function sum(x, y, z) {
  return x + y + z;
}

const numbers = [1, 2, 3];

console.log(sum(...numbers));
// Expected output: 6

console.log(sum.apply(null, numbers));
// Expected output: 6

```

here is how it cannot be used

```js
const obj = { key1: "value1" };
const array = [...obj]; // TypeError: obj is not iterable
```

===**A GREAT WAY TO TRANSFORM AN ARRAY INTO OBJECT**==

```JS
const array = [1, 2, 3];
const obj = { ...array }; // { 0: 1, 1: 2, 2: 3 }
```

Before spread syntex we had to use apply() but now we can do the same with spread syntax:

```js
function myFunction(x, y, z) {}
const args = [0, 1, 2];
myFunction.apply(null, args);
```

```js
function myFunction(x, y, z) {}
const args = [0, 1, 2];
myFunction(...args);
```

### Copying an array

```js
const arr = [1, 2, 3];
const arr2 = [...arr]; // like arr.slice()

arr2.push(4);
// arr2 becomes [1, 2, 3, 4]
// arr remains unaffected

```

### Concatenate arrays

```js 
let arr1 = [0, 1, 2];
const arr2 = [3, 4, 5];

arr1 = [...arr1, ...arr2];
// arr1 is now [0, 1, 2, 3, 4, 5]

```

