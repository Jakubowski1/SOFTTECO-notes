
```jsx
const people = [
  'Creola Katherine Johnson: mathematician',
  'Mario José Molina-Pasquel Henríquez: chemist',
  'Mohammad Abdus Salam: physicist',
  'Percy Lavon Julian: chemist',
  'Subrahmanyan Chandrasekhar: astrophysicist'
];

export default function List() {
  const listItems = people.map(person =>
    <li>{person}</li>
  );
  return <ul>{listItems}</ul>;
}

```

This loads an error

```error
Warning: Each child in a list should have a unique “key” prop.
```

To solve this issue we must give each array item a `key`. 

```js
<li key={person.id}>...</li>
```

### Filtering arrays of items

Let's work on such dataset

```jsx
const people = [
	{  
		id: 0,  
		name: 'Creola Katherine Johnson',  
		profession: 'mathematician',  
	}, {  
		id: 1,  
		name: 'Mario José Molina-Pasquel Henríquez',  
		profession: 'chemist',  
	}, {  
		id: 2,  
		name: 'Mohammad Abdus Salam',  
		profession: 'physicist',  
	}, {  
		id: 3,  
		name: 'Percy Lavon Julian',  
		profession: 'chemist',  
	}, {  
		id: 4,  
		name: 'Subrahmanyan Chandrasekhar',  
		profession: 'astrophysicist',  
}];
```

Now filter out the chemists with use of `filter()` and map over them to new array.

```jsx
import { people } from './data.js';
import { getImageUrl } from './utils.js';

export default function List() {
let chemists = people.filter(person => person.profession === 'chemist');

const listItems = chemist.map(peroson => 
	<li>
		<img src={getImageUrl(person)} alt={person.name}/>  
		<p><b>{person.name}:</b>  
		{' ' + person.profession + ' '}  
		known for {person.accomplishment}  
		</p>
	</li>						 
	);
	return(
	<ul>{listItem}</ul>
	);
}
```