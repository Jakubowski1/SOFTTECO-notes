#### Assignment operators

| [Assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Assignment)                                           | `x = f()`    | `x = f()`        |
| ---------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | ---------------- |
| [Addition assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Addition_assignment)                         | `x += f()`   | `x = x + f()`    |
| [Subtraction assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Subtraction_assignment)                   | `x -= f()`   | `x = x - f()`    |
| [Multiplication assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Multiplication_assignment)             | `x *= f()`   | `x = x * f()`    |
| [Division assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Division_assignment)                         | `x /= f()`   | `x = x / f()`    |
| [Remainder assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Remainder_assignment)                       | `x %= f()`   | `x = x % f()`    |
| [Exponentiation assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Exponentiation_assignment)             | `x **= f()`  | `x = x ** f()`   |
| [Left shift assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Left_shift_assignment)                     | `x <<= f()`  | `x = x << f()`   |
| [Right shift assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Right_shift_assignment)                   | `x >>= f()`  | `x = x >> f()`   |
| [Unsigned right shift assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Unsigned_right_shift_assignment) | `x >>>= f()` | `x = x >>> f()`  |
| [Bitwise AND assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Bitwise_AND_assignment)                   | `x &= f()`   | `x = x & f()`    |
| [Bitwise XOR assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Bitwise_XOR_assignment)                   | `x ^= f()`   | `x = x ^ f()`    |
| [Bitwise OR assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Bitwise_OR_assignment)                     | `x \|= f()`  | `x = x \| f()`   |
| [Logical AND assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_AND_assignment)                   | `x &&= f()`  | `x && (x = f())` |
| [Logical OR assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_OR_assignment)                     | `x \|= f()`  | `x \| (x = f())` |
| [Nullish coalescing assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Nullish_coalescing_assignment)     | `x ??= f()`  | `x ?? (x = f())` |

#### Destructuring

```js
const foo = ["one", "two", "three"];

const one = foo[0];
const two = foo[1];
const three = foo[2];
```

This can be done much simpler: 

```js
const [one, two, three] = foo;
```

#### Conditional (tenary) operator

```js
condition ? val1 : val2
```
If `condition` is true, the operator has the value of `val1`. Otherwise it has the value of `val2`. You can use the conditional operator anywhere you would use a standard operator.

#### Unary operators

The `delete` access object property
```js
delete object.property;
delete object[propertyKey];
delete objectName[index];
```
where `object` is the name of an object, `property` is an existing property, and `propertyKey` is a string or symbol referring to an existing property.

If the `delete` operator succeeds, it removes the property from the object. Trying to access it afterwards will yield `undefined`. The `delete` operator returns `true` if the operation is possible; it returns `false` if the operation is not possible.

#### in
The `in` operator returns true if the specified property is in the specified object. 
```js 
propNameOrNumber in objectName
```
==Remark==
```js
// Arrays
const trees = ["redwood", "bay", "cedar", "oak", "maple"];
0 in trees; // returns true
3 in trees; // returns true
6 in trees; // returns false
"bay" in trees; // returns false
// (you must specify the index number, not the value at that index)
"length" in trees; // returns true (length is an Array property)

// built-in objects
"PI" in Math; // returns true
const myString = new String("coral");
"length" in myString; // returns true

// Custom objects
const mycar = { make: "Honda", model: "Accord", year: 1998 };
"make" in mycar; // returns true
"model" in mycar; // returns true
```
#### instanceof
```js
objectName instanceof objectType

```
where `objectName` is the name of the object to compare to `objectType`, and `objectType` is an object type, such as `Date` or `Array`.
```js
const theDay = new Date(1995, 12, 17);
if (theDay instanceof Date) {
  // statements to execute
}
```

#### new

You can use the `new` operator to create an instance of a user-defined object type or of one of the built-in object types. Use `new` as follows:
```js
const objectName = new ObjectType(param1, param2, /* …, */ paramN);
```
