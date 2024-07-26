```
npm install --save-dev jest
```
``` package.json
{  
"scripts": {  
"test": "jest"  
}  
}
```
First test `sum.test.js`

```js
const sum = require('./sum');  
  
test('adds 1 + 2 to equal 3', () => {  
expect(sum(1, 2)).toBe(3);  
	});
```
