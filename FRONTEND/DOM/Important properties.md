
#### Style display property

Set a `<div>` not to be displayed

```js
document.getElementById("myDIV").style.display = "none";
```

The display property also allows the author to show or hide an element. It is similar to the visability property. However, if you set `display:none`, it hides the entire element, while `visibility:hidden` means that the contents of the element will be invisible, but the element stays in its original position and size.

```js
object.style.display = value
```

For example `block` to be displayed.

#### innerHTML

The element property that gets or sets the HTML.

Reading the contents of your element:

```js
let contents = myElement.innerHTML;
```

For example, you can erase the entire contents of a document by clearing the contents of the document's body attribute:

```js
document.body.innerHTML = "";
```

Or replace/ add something

```html
<ul id="list">
  <li><a href="#">Item 1</a></li>
  <li><a href="#">Item 2</a></li>
  <li><a href="#">Item 3</a></li>
</ul>

```

```js
const list = document.getElementById("list");

list.innerHTML += `<li><a href="#">Item ${list.children.length + 1}</a></li>`;

```