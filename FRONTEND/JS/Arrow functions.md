
They were introduced in ES6. They are notable for handling `this` keyword.

- Cannot be used as a constructor
- Cannot be used as a generator
#### Syntax 

```js
() => expression

param => expression

(param) => expression

(param1, paramN) => expression

() => {
  statements
}

param => {
  statements
}

(param1, paramN) => {
  statements
}
```

Examples 
```js
(a, b, ...r) => expression
(a = 400, b = 20, c) => expression
([a, b] = [10, 20]) => expression
({ a, b } = { a: 10, b: 20 }) => expression
```

More examples
1) 
```js
// Traditional anonymous function
(function (a) {
  return a + 100;
});

// 1. Remove the word "function" and place arrow between the argument and opening body brace
(a) => {
  return a + 100;
};

// 2. Remove the body braces and word "return" — the return is implied.
(a) => a + 100;

// 3. Remove the parameter parentheses
a => a + 100;

```

2) 

```js
// Traditional anonymous function
(function (a, b) {
  return a + b + 100;
});

// Arrow function
(a, b) => a + b + 100;

const a = 4;
const b = 2;
```

3) 
```js
// Traditional anonymous function (no parameters)
(function () {
  return a + b + 100;
});

// Arrow function (no parameters)
() => a + b + 100;

```

4) 
```js
// Traditional anonymous function
(function (a, b) {
  const chuck = 42;
  return a + b + chuck;
});

// Arrow function
(a, b) => {
  const chuck = 42;
  return a + b + chuck;
};

```

5) 
```js
// Traditional Function
function bob(a) {
  return a + 100;
}

// Arrow Function
const bob2 = (a) => a + 100;

```

Arrow functions implicitly return the expression right after `=>`, so you didn’t need a `return` statement:

```js
const listItems = chemists.map(person => 
<li>...</li> 
					// Implicit return!
);
```

However, **you must write `return` explicitly if your `=>` is followed by a `{` curly brace!**

```js
const listItems = chemists.map(person => { 
						// Curly brace  
return <li>...</li>;
});
```

Arrow functions containing `=> {` are said to have a block body. They let you write more than a single line of code, but you _have to_ write a `return` statement yourself. If you forget it, nothing gets returned!