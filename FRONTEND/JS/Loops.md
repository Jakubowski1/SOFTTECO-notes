
### for

```js
for (initialization; condition; afterthought)
  statement
```

### do ... while

```js
do
  statement
while (condition);
```

### while

```js
while (condition)
  statement
```

### labeled

A statement with an identifier that lets you refer to it elsewhere in your program.
```js
label:
  statement
```

### break

```js
break; //terminates current loop from running
break label; //terminates an exact label statement that was running
```

==IMPORTANT FOR UNDERSTANDING THIS==

```js
let x = 0;
let z = 0;
labelCancelLoops: while (true) {
  console.log("Outer loops:", x);
  x += 1;
  z = 1;
  while (true) {
    console.log("Inner loops:", z);
    z += 1;
    if (z === 10 && x === 10) {
      break labelCancelLoops;
    } else if (z === 10) {
      break;
    }
  }
}
```

### continue
 
 It is an opposite to break. Restarts stuff.

  ```js
continue;
continue label;

```

### for ... in

```js
for (variable in object)
  statement
```

```js
function dumpProps(obj, objName) {
  let result = "";
  for (const i in obj) {
    result += `${objName}.${i} = ${obj[i]}<br>`;
  }
  result += "<hr>";
  return result;
}
```

### for ... of

```js
for (variable of object)
  statement
```

```js
const arr = [3, 5, 7];
arr.foo = "hello";

for (const i in arr) {
  console.log(i);
}
// "0" "1" "2" "foo"

for (const i of arr) {
  console.log(i);
}
// Logs: 3 5 7
```

```js
const obj = { foo: 1, bar: 2 };

for (const [key, val] of Object.entries(obj)) {
  console.log(key, val);
}
// "foo" 1
// "bar" 2

```