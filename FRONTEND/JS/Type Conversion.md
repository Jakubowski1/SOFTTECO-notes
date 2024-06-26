
Proper conversion with the Unary + Operator
```js
let y = "5"; // it is a string
let x = + y; //it is a number
```

Example of something that cannot be converted
```js
 let y = "John";
 let x = + y;  // x is not a number
```

Number Methods

	- Number() Returns a number,  converted from its argument
	- parseFloat() Parses a string and returns a floating point number
	- parseInt() Parses a string and return an integer

Converting numbers to strings

```js
x.toString();
String(x); //they work the same
String(Date())  // returns "Thu Jul 17 2014 15:38:19 GMT+0200 (W. Europe Daylight Time)"
```

Automatic type conversion

```js
5 + null    // returns 5         because null is converted to 0  
"5" + null  // returns "5null"   because null is converted to "null"  
"5" + 2     // returns "52"      because 2 is converted to "2"  
"5" - 2     // returns 3         because "5" is converted to 5  
"5" * "2"   // returns 10        because "5" and "2" are converted to 5 and 2
```