[[Arrow functions]]
### Function declaration
#### Syntax
```js
function _functionName_(_param1_, _param2_, ..., _paramN_){ 
// Function's body 
}
```

### Function expression

#### Syntax

```js
var _identifierName_ = function [_functionName_](_param1_, _param2_, ..., _paramN_) { // Function's body }
```

Here is a cool representation of how this can potentially be used:

a) stored as an array

```js
var utils = [
   function(a, b) { return a + b; },
   function(a, b) { return a - b; }
];

console.log(utils[0](10, 20));
console.log(utils[1](50, 5));
```

b) stored ad an object

```js
var utils = {
   add: function(a, b) { return a + b; },
   diff: function(a, b) { return a - b; }
}

console.log(utils.add(10, 20));
console.log(utils.diff(50, 5));
```


### Callback

A function passed to another function as an argument.

```js
function execute(fn) {
   fn();
}

execute(function() { console.log('Hello World!'); })
```

### Function declaration vs Function expression

1) The function declarations are a subject to functional hoisting whereas functional expressions are not. Below example:

```js
console.log(sum(3,5));
function sum(a, b){
return a+b;
}
//This code should work just fine
```

```js
console.log(sum(3,5));

var sum = function(a, b){
return a+b;
}
//Uncaught TypeError: sum is not a function
```

2) Leaving out the name of a function is only possible with a function expression. Which means **anonymous functions** can be created solely by function expressions. 

### **_IIFE_**, or an **_Immediately Invoked Function Expression_**.

```js
(function() {
   console.log('I am in an IIFE.')
})();
```

Yeah, cool but why do I need that?

```html
<html>
<head>
   <!-- ... -->
</head>
<body>
   <!-- ... -->
   <script src="lib1.js"></script>
   <script src="lib2.js"></script>
</body>
</html>
```

```js
// lib1.js
(function() {
   var main;
   // ...
})();
```


```js
// lib2.js
(function() {
   var main;
   // ...
})();
```

Each library has its code encapsulated inside an IIFE and likewise doesn't at all interfere with the code of the other one. _Simply amazing._


### Named function expressions

So the main question is since I can use the name of the identifier why do I need a name for function ?

```js
var nums = [1, 2, 3];
var squares = nums.map(function toSquare(num) { return num ** 2; });

console.log(squares);
```

Not sure if I get it ://
#### arguments.callee

The expression `arguments.callee`, when used inside a function, simply refers to the function itself.

```js
var nums = [1, 2, 3, 4, 5, 6];

var fibs = nums.map(function(n) {
   if (n === 1) return 0;
   if (n === 2) return 1;
   return arguments.callee(n - 1) + arguments.callee(n - 2);
});

console.log(fibs);
```

