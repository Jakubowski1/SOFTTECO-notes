Reducer is a function which takes two arguments -- the current state and an action -- and returns based on both arguments a new state.

Remember what defines it:
- **Immutability:** State is never changed directly. Instead the reducer always creates a new state.

```
(state, action) => newState
```

Simple example:
```js
function counterReducer(state, action) {
  return state + 1;
}
```

```js
expect(counterReducer(0)).to.equal(1); // successful test
```

A bit more complex here: 

```js
const counterReducer = (count, action) => {
  if (action.type === 'INCREASE') {
    return count + 1;
  }
  if (action.type === 'DECREASE') {
    return count - 1;
  }
  return count;
};
```

It is pretty easy to test
```js
// successful tests
// because given the same input we can always expect the same output
expect(counterReducer(0, { type: 'INCREASE' })).to.equal(1);
expect(counterReducer(0, { type: 'INCREASE' })).to.equal(1);
// other state transition
expect(counterReducer(0, { type: 'DECREASE' })).to.equal(-1);
// if an unmatching action type is defined the current state is returned
expect(counterReducer(0, { type: 'UNMATCHING_ACTION' })).to.equal(0);
```

The same function using switch logic:

```js
const counterReducer = (count, action) => {
  switch (action.type) {
    case 'INCREASE':
      return count + 1;
    case 'DECREASE':
      return count - 1;
    default:
      return count;
  }
};
```

Below let's manipulate an object

```js
const personReducer = (person, action) => {
  switch (action.type) {
    case 'INCREASE_AGE':
      return { ...person, age: person.age + 1 };
    case 'CHANGE_LASTNAME':
      return { ...person, lastname: action.lastname };
    default:
      return person;
  }
};
```

And how do I use this function and it what case? Here is why and when:

```js
const initialState = {
  firstname: 'Liesa',
  lastname: 'Huppertz',
  age: 30,
};
const action = {
  type: 'CHANGE_LASTNAME',
  lastname: 'Wieruch',
};
const result = personReducer(initialState, action);
expect(result).to.equal({
  firstname: 'Liesa',
  lastname: 'Wieruch',
  age: 30,
});
```