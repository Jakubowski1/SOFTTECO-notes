
The `Node` interface is extremely useful. It contains a great deal of properties and methods to help us operate on a given node in various ways.

|Property|Purpose|
|---|---|
|**`textContent`**|The textual content of the given node. Depends on the type of the node.|
|**`nodeType`**|An integer representing the type of the node.|
|**`nodeName`**|A string representing the name of the node.|
|**`nodeValue`**|A string representing the value of the node.|
|**`parentNode`**|A reference to the parent node of the given node.|
|**`childNodes`**|An `NodeList` instance containing all the child nodes of the given node.|
|**`firstChild`**|A reference to the first child node of the given node.|
|**`lastChild`**|A reference to the last child of the given node.|
|**`nextSibling`**|A reference to the next sibling of the given node, i.e. the one that comes after it in the HTML source code.|
|**`previousSibling`**|A reference to the previous sibling of the given node, i.e. the one that comes before it in the HTML source code.|
|**`ownerDocument`**|A reference to the `document` object that owns the given node.|

Now, let's talk about the methods of the `Node` interface:

| **Method**           | **Purpose**                                                                |
| -------------------- | -------------------------------------------------------------------------- |
| **`appendChild()`**  | Adds a node inside the calling node as its last child.                     |
| **`insertBefore()`** | Adds a node inside the calling node before a reference child node.         |
| **`replaceChild()`** | Replace a particular child node inside the calling node with another node. |
| **`removeChild()`**  | Remove a particular child node from the calling node.                      |
| **`cloneNode()`**    | Make a copy of the calling node.                                           |

each of them hold an integer

|Constant|Value|Purpose|
|---|---|---|
|**`ELEMENT_NODE`**|`1`|Represents the element node type.|
|**`ATTRIBUTE_NODE`**|`2`|Represents the attribute node type.|
|**`TEXT_NODE`**|`3`|Represents the text node type.|
|**`COMMENT_NODE`**|`8`|Represents the comment node type.|
|**`DOCUMENT_NODE`**|`9`|Represents the (root) document node type.|
|**`DOCUMENT_TYPE_NODE`**|`10`|Represents the document-type node type.|
|**`DOCUMENT_FRAGMENT_NODE`**|`11`|Represents the document fragment node type.|

Example
```html
<div id="main">
   <p>A paragraph</p>
   <!--A comment-->
</div>
```

```js
var mainElement = document.getElementById('main');

for (var i = 0, len = mainElement.childNodes.length; i < len; i++) {
   console.log(mainElement.childNodes[i].nodeName);
}
```

```js
//#text P #text #comment #text
```

### The `firstChild` and `lastChild` properties

Keep in mind that for a given node _`n`_, `_n_.firstChild` is functionally equivalent to `_n_.childNodes[0]` while `_n_.lastChild` is functionally equivalent to `_n_.childNodes[_n_.childNodes.length - 1]`.

```js
var mainElement = document.getElementById('main');

console.log(mainElement.firstChild.nodeName);
console.log(mainElement.lastChild.nodeName);

//#text #text
```

### The `nextSibling` and `previousSibling` properties

If there is no sibling after or before a given node in the HTML markup, `nextSibling` and `previousSibling` return `null`.
```js
var mainElement = document.getElementById('main');

console.log(mainElement.firstChild.nextSibling.nodeName);

//P
```

### The `parentNode` property

```js
var node = document.getElementById('main').firstChild;

console.log(node.nodeName);
console.log(node.parentNode.nodeName);
console.log(node.parentNode.parentNode.nodeName);
console.log(node.parentNode.parentNode.parentNode.nodeName);
console.log(node.parentNode.parentNode.parentNode.parentNode.nodeName);

//#text 
//DIV 
//BODY
//HTML 
//#document
```

### `nodeName` property
```html
<div id="main">
   <p>A paragraph</p>
   <!--A comment-->
</div>
```

```js
var mainElement = document.getElementById('main');

if (mainElement.nodeName === 'P') {
   console.log('Yes');
}
else {
   console.log('No');
}
```

### The `nodeValue` property

- For text nodes, it returns the textual content of the node.
- For comment nodes, returning back the textual content of the comment (excluding the comment tags).
- For element nodes, it returns `null`.
- For document nodes, it returns `null`.
- For document fragment nodes, it returns `null`.

### The `nodeType` property

| Value | Meaning                                                       |
| ----- | ------------------------------------------------------------- |
| `1`   | Represents an `Element` node.                                 |
| `2`   | Represents an `Attr` node.                                    |
| `3`   | Represents a `Text` node.                                     |
| `4`   | Represents a `CDATASection` node.                             |
| `5`   | Represents a `ProcessingInstruction` node of an XML document. |
| `6`   | Represents a `Comment` node.                                  |
| `7`   | Represents a `Document` node.                                 |
| `8`   | Represents a `DocumentType` node.                             |
| `9`   | Represents a `DocumentFragment` node.                         |

### Factory methods to create nodes

#### **`createElement()`**
```js
var divElement = document.createElement('div');
divElement.innerHTML = 'A div node';

var mainElement = document.getElementById('main');

// Add the <div> element inside #main.
mainElement.appendChild(divElement);
```

#### `createTextNode()`
 
```js
var mainElement = document.getElementById('main');

var textNode = document.createTextNode('A div node');

mainElement.appendChild(textNode);
```

#### `createDocumentFragment()`

```js
var h1Element = document.createElement('h1');
h1Element.innerHTML = 'A heading';

var paraElement = document.createElement('p');
paraElement.innerHTML = 'A paragraph';

var fragment = document.createDocumentFragment();
fragment.appendChild(h1Element);
fragment.appendChild(paraElement);

var mainElement = document.getElementById('main');
mainElement.appendChild(fragment);
```