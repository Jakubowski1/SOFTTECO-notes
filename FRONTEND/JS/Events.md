
```html
<element event="some JavaScript">
```

| Event       | Description                                        |
| ----------- | -------------------------------------------------- |
| onchange    | An HTML element has been changed                   |
| onclick     | The user clicks an HTML element                    |
| onmouseover | The user moves the mouse over an HTML element      |
| onmouseout  | The user moves the mouse away from an HTML element |
| onkeydown   | The user pushes a keyboard key                     |
| onload      | The browser has finished loading the page          |

### Event's target

The **_target_** is simply an object on which the event takes place.
### Event's handler
An event's **_handler function_**, or simply **_handler_**, is a function set up by the developer to handle the event, when it occurs.

```js
var buttonElement = document.querySelector('button');

function handler1() { /* ... */ }
function handler2() { /* ... */ }

buttonElement.onclick = function() {
   handler1();
   handler2();
}
```

### `addEventListener()`

Add an event listener that fires when a user clicks a button:

```js
document.getElementById("myBtn").addEventListener("click", displayDate);
```

Syntax

```js
element.addEventListener(_event, function, useCapture);
```

The third parameter is a boolean value specifying whether to use event bubbling or event capturing. This parameter is optional.


### Event Bubbling

Event bubbling is a type of event propagation in the DOM where an event starts at the target element and then bubbles up to the root of the DOM tree. This means that if an event is triggered on an element, it first runs the handlers on that element, then on its parent, then on its parent's parent, and so on, until it reaches the `document` object.

So basically you click a child the parent is triggered. 

### Event Delegation

The idea is that you "**delegate**" the handling of an event to a different element (in this case, the div, which is a parent element) instead of the actual element (the button) that received the event.

```js
const div = document.getElementsByTagName("div")[0]

div.addEventListener("click", (event) => {
  if(event.target.tagName === 'BUTTON') {
    console.log("button was clicked")
  }
})
```

With event delegation, you create fewer event listeners and perform similar events-based logic in one place