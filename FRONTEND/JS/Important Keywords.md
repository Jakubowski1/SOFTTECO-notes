### this

When used inside a function, **`this`** refers to the **object** that **called** the function.

#### Global Context

When a function object is called directly, not as part of an object, its `this` value resolves down to the global `window` object, given that the script is running in non-strict mode.

```js
console.log(this); // In browser, this will log the window object and in Node.js global
```

Here is an interesting situation happening. There is no actual object calling the function so `this.x` corresponds to `window.x`, which in this case looks for a globally declared variable (in this case x=10). THIS GOTTA BE IN NON-STRICT MODE

```js
function f() {
   console.log(this.x);
}

var x = 10;
f();
```
#### Example

```js
var o = {
   x: 10,
   f: function() { console.log(this.x); } //meaning o.x
};

var x = 20;
o.f();
```

### async

#### Yield

**Yield**: Inside the `getSides` method, the `yield` keyword is used to produce a sequence of values. Each call to `yield` pauses the function and returns the specified value to the caller.
**Iterator**: When you call `square.getSides()`, it returns an iterator. You can then use this iterator to get the values one by one, or you can use the spread operator (`...`) to ==convert the iterator into an array.==
```js
class Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
  // Getter
  get area() {
    return this.calcArea();
  }
  // Method
  calcArea() {
    return this.height * this.width;
  }
  *getSides() {
    yield this.height;
    yield this.width;
    yield this.height;
    yield this.width;
  }
}

const square = new Rectangle(10, 10);

console.log(square.area); // 100
console.log([...square.getSides()]); // [10, 10, 10, 10]

```

#### bind

When you call `bind` on a function, it returns a new function with a specific `this` value. Additionally, you can pass arguments to `bind` that will be prepended to the arguments provided to the bound function when it is invoked.

```js
const person = {
  name: 'Alice',
  greet: function() {
    console.log('Hello, my name is ' + this.name);
  }
};

const greet = person.greet;
greet(); // Hello, my name is undefined

const boundGreet = greet.bind(person);
boundGreet(); // Hello, my name is Alice

```

Prepending arguments

```js
function add(a, b) {
  return a + b;
}

const addFive = add.bind(null, 5);
console.log(addFive(10)); // 15

```

Using bind in class context

```js
class Button {
  constructor(text) {
    this.text = text;
    this.click = this.click.bind(this); // Ensure `this` refers to the instance
  }

  click() {
    console.log('Button ' + this.text + ' clicked');
  }
}

const button = new Button('Submit');
document.getElementById('myButton').addEventListener('click', button.click);

```

#### super

It is used to call functions on an object's parent class.

Exemplary usage:

```js
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} makes a noise.`);
  }
}

class Dog extends Animal {
  constructor(name, breed) {
    super(name); // Calls the constructor of Animal
    this.breed = breed;
  }

  speak() {
    super.speak(); // Calls the speak method of Animal
    console.log(`${this.name} barks.`);
  }
}

const myDog = new Dog('Rex', 'German Shepherd');
myDog.speak();
// Output:
// Rex makes a noise.
// Rex barks.

```

