Remember arrays are a object type

```js
var arr = [1, 2];

console.log(typeof arr); //object
```
### Adding at the end of an array

```js
var nums = [1, 2, 3];

nums[nums.length] = 10; // nums is now [1, 2, 3, 10]
nums[nums.length] = 20; // nums is now [1, 2, 3, 10, 20]
nums[nums.length] = 30; // nums is now [1, 2, 3, 10, 20, 30]

console.log(nums);
```

also

```js
var nums = [1, 2, 3];

nums[3] = 10;
nums[4] = 20;
nums[5] = 30;

console.log(nums);
```

also

```js
var nums = new Array(1, 2, 3);

nums.push(10);
nums.push(20);
nums.push(30);

console.log(nums);
```

#### `unshift()`

The **`unshift()`** method **adds** an element to the **start of an array**.

```js
var nums = [1, 2];

nums.unshift(3);
console.log(nums);
//[3, 1, 2]
```
#### `push()`

The **`push()`** method **adds** an element to the **end of an array**.

```js
var nums = [1, 2];

nums.push(3);
console.log(nums);
//[1, 2, 3]
```
### Removing elements from an array

#### `pop()` - last element

```js
var nums = [1, 2, 3];

nums.pop();
console.log(nums.length);
```

#### `shift()` - first element

```js
var nums = [1, 2, 3];

nums.shift();
console.log(nums.length);
```

### Creating an empty array

```js
var nums = new Array(3);

console.log(nums);// [empty x 3]
```

### Mutability of arrays

They are mutable.

```js
var nums = [1, 2, 3];
nums[1] = 10;

console.log(nums); // [1,10,3]
```

On the other hand remember `string` is not

```js
var str = 'Good';
str[0] = 'F';

console.log(str) //Good
```

### 2d array

```js
var arr = [[1, 2], [5, 3]]; // a 2d array

console.log(arr[0][0]); // 1
console.log(arr[0][1]); // 2
console.log(arr[1][0]); // 5
console.log(arr[1][1]); // 3

```

### isArray()

```js
Array.isArray([])
```

true

```js
Array.isArray([1, 2, 3])
```

true

```js
Array.isArray(null)
```

false

```js
Array.isArray(true)
```

false

```js
Array.isArray({0: 1, 1: 2})
```

false
