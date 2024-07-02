### `at(index)`

This method simply returns a value assigned to the index. 

### `concat()`

```js
var a = [75, 54, 70];
var b = [94, 60, 78];
var c = [67, 80, 81];

var allNums = a.concat(b, c);
console.log(allNums.sort());
```
### `fill()`

```js
[1, 2, 3, 4].fill(0)


//[0, 0, 0, 0]

```

```js
[1, true, 'Hello'].fill(100)
//[100,100,100]
```

It does not work with an empty array

```js
[].fill(0)
//[]
```

### `slice()

The **`slice()`** method takes a **starting** ==(inclusive)== and **ending index** ==(exclusive)== and returns a **copy of the array** in that range.

```js
var nums = [1, 2, 3, 4, 5];

console.log(nums.slice(0, 0)); // []
console.log(nums.slice(0, 1)); // [1]
console.log(nums.slice(1, 4)); // [2, 3, 4]
```

Notice how you can remove a specific index with this method. 

splice(index, how many jumps forward)

```js
var arr = [1, 50, -6, -20, 22];
var deletedArr = arr.splice(1, 1);

console.log(arr); //[1, -6, -20, 22]
console.log(deletedArr); // [50]
```

This means we can also go from the negative indexes 
```js
var arr = [1, 50, -6, -20, 22];
var deletedArr = arr.splice(-2, 1);

console.log(arr);
console.log(deletedArr);

//[1, 50, -6, 22]  
//[-20]
```

What if we want to remove nothing from an array, but rather add two elements at the second position? 

We'll call `arr.splice(1, 0, _ele1_, _ele2_)`.

```js
var arr = [1, 50, -6, -20, 22];
var deletedArr = arr.splice(1, 0, 'Hello', 'World!');

console.log(arr);
console.log(deletedArr);
// [1, "Hello", "World!", 50, -6, -20, 22]  
// []
```
#### reverse()

```js
var subs = ["Chem", "Physics", "Math"];


console.log(subs.reverse());

["Math", "Physics", "Chem"]
```

### `indexOf()` and `lastIndexOf()`

if they do not find a value it returns `-1`

```js
[1, 2, 3, 4].indexOf(1)
//0

[1, 2, 3, 4].indexOf(4)
//3

[1, 2, 3, 4].indexOf(5)
//-1 

[1, 2, 3, 4].indexOf("1")
//-1

[1, true, true, false].indexOf(true)
//1
```

#### `some()`

Slightly more complex. The method **`some()`** takes a function and returns `true` if the function evaluates to `true` for **at least one element** in the calling array.

Syntax

```js
arr.some(callbackFn)
//callbackFn(element, index, array, thisValue)
```

```js
function isSquare(element) {
   return Number.isInteger(element ** 0.5);
}

var nums = [1, 2, 3];
console.log(`Square in ${nums}`, nums.some(isSquare));

nums = [2, 3, 4];
console.log(`Square in ${nums}`, nums.some(isSquare));

nums = [2, 3, 5, 7];
console.log(`Square in ${nums}`, nums.some(isSquare));

nums = [2, 3, 5, 7, 49, 100];
console.log(`Square in ${nums}`, nums.some(isSquare));


//Square in [1, 2, 3]: true  
//Square in [2, 3, 4]: true  
//Square in [2, 3, 5, 7]: false  
//Square in [2, 3, 5, 7, 49, 100]: true
```

Different idea

```js
function isSquare(element) {
   return Number.isInteger(element ** 0.5);
}

console.log([].some(isSquare)); //false
```

#### `every()`

Similar to it's predecessor

```js
function above50(marks) {
   return marks >= 50;
}

var marksList = [35, 80, 54, 90, 60];
console.log(marksList.every(above50)); //false

marksList = [78, 86, 70, 95, 71];
console.log(marksList.every(above50)); //true
```

```js
function above50(marks) {
   return marks >= 50;
}

console.log([].every(above50)); //true
```

#### `filer()`

Cool shit

```js
function positiveNumber(num) {
   return num > 0;
}

var nums = [10, 5, -4, -1, 50, 34, -27];
console.log(nums.filter(positiveNumber));

nums = [0, 15, 0, -6, -1, -4, -0.5, 3.1, 10.5];
console.log(nums.filter(positiveNumber));
```

```js
var nums = [1, 10, 5, 33, 198, 0, 5, 8];

function skip(num, index){
    return index % 2 === 0; // Check if the index is even
}

var evenIndexes = nums.filter(skip);

console.log(evenIndexes); // [1, 5, 198, 5]

```

### Joining elements

```js
[1, 2, 3, 4].toString() //1,2,3,4
[1, 2, 3, 4] + '' //1,2,3,4
'The numbers are: ' + [1, 2, 3, 4] //The numbers are: 1,2,3,4
```

Yeah but how do I do it without those commas?

`join(delimiter)`

```js
var nums = [1, 2, 10, 50, 100];

console.log(nums.join(' '));

//1 2 10 50 100
```

### Mapping an array by `map()`

Calling `map()` on an array does not mutate it.

```js
function toSquare(int) { return int ** 2 };
function toCube(int) { return int ** 3 };

var ints = [0, 1, 2, 3, 4, 5];

var squares = ints.map(toSquare);
console.log(squares);

var cubes = ints.map(toCube);
console.log(cubes);

// let's see if ints has been modified
console.log(ints);
```

Crazy usage, convert a string to an array

```js
var str = '10 -5 40 1 0 0 3';

var nums = str.split(' ').map(Number)

console.log(nums);
	//[10, -5, 40, 1,   0,  0,  3]
```