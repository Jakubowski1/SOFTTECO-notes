
```js
var variableName = value;
```


```js
var text = "The ' character is called an apostrophe.";
console.log(text);
```

#### Use strict
In order to get our code to throw errors when we forget to correct such clerical typos, JavaScript provides us with a **_strict mode_**. A program could be entered into strict mode by using `'use strict'` at the start of the script.

```js
'use strict'

var x = 10;
    y = 20,
    z = 30;

console.log(x + y + z);
```

```console
Uncaught ReferenceError: y is not defined
```

### Brain teaser
```js
var x = 10;
var y = '5';

```
#### typeof

```js
typeof [1, 2, 3]; // 'object'
typeof null; //'object'
typeof {}; // 'object'
typeof {x: 10}; // 'object'

typeof 10; // 'number'
typeof 3.142; // 'number'

typeof "Hello"; // 'string'
typeof 'Hello'; // 'string'

typeof true; // 'boolean'

typeof undefined; // 'undefined'

typeof function() {}; // "function"
```



Value is the value whose type we ought to determine.

When provided with a non-existent variable, typeof returns the string 'undefined'. 


```js
console.log(typeof x != 'undefined');

var y;
console.log(typeof y != 'undefined');
```

```console
false 
false
```

#### Changing types on the fly - Dynamically typed language

In JavaScript, we don't have to (and in fact, even can't) declare the types of variables upfront. During the course of a program, we can easily change the types of values stored in a variable, and the interpreter won't complaint even for a second.

The code below illustrates this:

```js
// x is a number
var x = 10;

// x is now a string
x = "Hello";

// x is now a Boolean
x = false;
```
#### The `let` keyword

The **`let`** keyword was introduced in JavaScript with the advent of ECMAScript 6. It's a new way of defining variables.

In particular, `let` creates **_block-scoped_** variables. In contrast, `var` does not create block-scoped variables. We'll explore variable scopes at length in the variable scoping and it's there that we'll reiterate on this idea of block-scoped variables created using `let`.

-`let`declarations are not hoisted

## Data Types

#### Primitives

- undefined
- null
- numbers
- strings
- Booleans
#### Object data types

- **Arrays**
	```js
var nums = [1, -5, 10];
console.log(nums.length);
>> 3
nums[-1];
>>undefined
nums.sort();
>> [-5,1,10];
```
- **Functions**
	```js
function sayHello() {
   var name = prompt('Enter your name:');
   document.write('Hello, ' + name + '.');
}
```

- **Objects**
	```js
var url = {
   protocol: 'https',
   domain: 'www.codeguage.com',
   path: '/'
};```

An **_object_** is a value composed of primitives.

```js
url['protocol']
>> 'https'
url.protocol
>> 'https'
```

Now I add couple modifications

```js
var url = {
   protocol: 'https',
   domain: 'www.codeguage.com',
   path: '/',

   // return the full URL, as a string
   getURL: function() {
      return url.protocol + '://' + url.domain + url.path;
   }
};
```

```console 
url.getURL()

'https://www.codeguage.com/'
```

When you try to call from an object something that does not exist, you can declare it like this. 

```js
// add two new properties
url.queryString = null;
url['hash'] = null;
```

The same but with different declaration 

```js
const obj = {};

obj.x = 3;
console.log(obj.x); // Prints 3.
console.log(obj); // Prints { x: 3 }.

const key = "y";
obj[key] = 5;
console.log(obj[key]); // Prints 5.
console.log(obj); // Prints { x: 3, y: 5 }.
```
#### Autoboxing 

Simply when JavaScript automatically boxes, i.e. wraps, a primitive value into an object based on its corresponding ==wrapper class==.

1. `Number` for numbers
2. `String` for strings
3. `Boolean` for Booleans
4. `BigInt` for big integers
5. `Symbol` for symbols

#### Symbol

```js
const sym = Symbol("foo");
typeof sym; // "symbol"
const symObj = Object(sym);
typeof symObj; // "object"
```

#### BigInt

**`BigInt`** values represent numeric values which are too large to be represented by the `number` primitive.
#### Get

```js
//Syntax
{ get prop() { /* … */ } }
{ get [expression]() { /* … */ } }
```


```js
const obj = {
  log: ['a', 'b', 'c'],
  get latest() {
    return this.log[this.log.length - 1];
  },
};

console.log(obj.latest);
// Expected output: "c"
```

### Object properties

#### Data property

`value`
The value retrieved by a get access of the property. Can be any JavaScript value.

`writable`
A boolean value indicating if the property can be changed with an assignment.

`enumerable`
A boolean value indicating if the property can be enumerated by a loop for example. 

`configurable`
A boolean value indicating if the property can be deleted, can be changed to an accessor property, and can have its attributes changed.

#### Accessor property

Associates a key with one of two accessor functions (`get` and `set`) to retrieve or store a value.

`get`
A function called with an empty argument list to retrieve the property value whenever a get access to the value is performed. 

`set`
A function called with an argument that contains the assigned value. Executed whenever a specified property is attempted to  be changed. 

`enumerable`
A boolean value indicating if the property can be enumerated by a loop for example. 

`configurable`
A boolean value indicating if the property can be deleted, can be changed to an accessor property, and can have its attributes changed.


