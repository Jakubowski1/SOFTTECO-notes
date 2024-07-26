Good example with conditional rendering
```js
function Item({ name, isPacked }) {
  return (
    <li className="item">
      {name} {isPacked && '✔'}
    </li>
  );
}

export default function PackingList() {
  return (
    <section>
      <h1>Sally Ride's Packing List</h1>
      <ul>
        <Item 
          isPacked={true} 
          name="Space suit" 
        />
        <Item 
          isPacked={true} 
          name="Helmet with a golden leaf" 
        />
        <Item 
          isPacked={false} 
          name="Photo of Tam" 
        />
      </ul>
    </section>
  );
}

```

Remember you can also use logical statements

```jsx
function Drink({ name }) {
  let part, caffeine, age;
  if (name === 'tea') {
    part = 'leaf';
    caffeine = '15–70 mg/cup';
    age = '4,000+ years';
  } else if (name === 'coffee') {
    part = 'bean';
    caffeine = '80–185 mg/cup';
    age = '1,000+ years';
  }
  return (
    <section>
      <h1>{name}</h1>
      <dl>
        <dt>Part of plant</dt>
        <dd>{part}</dd>
        <dt>Caffeine content</dt>
        <dd>{caffeine}</dd>
        <dt>Age</dt>
        <dd>{age}</dd>
      </dl>
    </section>
  );
}

export default function DrinkList() {
  return (
    <div>
      <Drink name="tea" />
      <Drink name="coffee" />
    </div>
  );
}

```

### enum conditional rendering logic

Basically it is a switch statement on steroids because it can be used within jsx.

```js
function Message({ isExtrovert, isVegetarian }) {
  const key = `${isExtrovert}-${isVegetarian}`;

  return (
    <div>
      {
        {
          'true-true': <p>I am an extroverted vegetarian.</p>,
          'true-false': <p>I am an extroverted meat eater.</p>,
          'false-true': <p>I am an introverted vegetarian.</p>,
          'false-false': <p>I am an introverted meat eater.</p>,
        }[key]
      }
    </div>
  );
}
```

### HOC's - Higher Order Components

- if
    - most basic conditional rendering
    - use to opt-out early from a rendering (guard pattern)
    - cannot be used within return statement and JSX (except self invoking function)
- if-else
    - use it rarely, because it's verbose
    - instead, use ternary operator or logical && operator
    - cannot be used inside return statement and JSX (except self invoking function)
- ternary operator
    - use it instead of an if-else statement
    - it can be used within JSX and return statement
- logical && operator
    - use it when one side of the ternary operation would return null
    - it can be used inside JSX and return statement
- switch case
    - avoid using it, because it's too verbose
    - instead, use enums
    - cannot be used within JSX and return (except self invoking function)
- enums
    - use it for conditional rendering based on multiple states
    - perfect to map more than one condition
- nested conditional rendering
    - avoid them for the sake of readability
    - instead, split out components, use if statements, or use HOCs
- HOCs
    - components can focus on their main purpose
    - use HOC to shield away conditional rendering
    - use multiple composable HOCs to shield away multiple conditional renderings
- external templating components
    - avoid them and be comfortable with JSX and JS


## ==Remark==

**Don’t put numbers on the left side of `&&`.**

For example, a common mistake is to write code like `messageCount && <p>New messages</p>`. It’s easy to assume that it renders nothing when `messageCount` is `0`, but it really renders the `0` itself!

