### Keyed collections


#### Maps

The **`Map`** object holds key-value pairs and remembers the original insertion order of the keys. Any value (both objects and primitives) may be used as either a key or a value.

```js
const map1 = new Map();

map1.set('a', 1);
map1.set('b', 2);
map1.set('c', 3);

console.log(map1.get('a'));
// Expected output: 1

map1.set('a', 97);

console.log(map1.get('a'));
// Expected output: 97

console.log(map1.size);
// Expected output: 3

map1.delete('b');

console.log(map1.size);
// Expected output: 2

```

`Map()` is a constructor which creates a new map object.

##### Instance methods in maps

`map1.clear()`
Removes all key-value pairs from the `Map` object.

`map1.delete()`
Returns `true` if an element in the `Map` object existed and has been removed, or `false` if the element does not exist. `map.has(key)` will return `false` afterwards.

`map1.entries()`
Returns a new Iterator object that contains a two-member array of `[key, value]` for each element in the `Map` object in insertion order.

`map1.froEach()
Calls `callbackFn` once for each key-value pair present in the `Map` object, in insertion order. If a `thisArg` parameter is provided to `forEach`, it will be used as the `this` value for each callback.
```js
myMap.forEach((value, key) => {
  console.log(`${key} = ${value}`);
});
// 0 = zero
// 1 = one
```
`map1.get()`
Returns the value associated to the passed key, or `undefined` if there is none.

`map1.has()`
Returns a boolean indicating whether a value has been associated with the passed key in the `Map` object or not.

`map1.keys()`
Returns a new Iterator object that contains the keys for each element in the `Map` object in insertion order.

`map1.set()`
Sets the value for the passed key in the `Map` object. Returns the `Map` object.

`map1.values()`
Returns a new Iterator object that contains the values for each element in the `Map` object in insertion order.

`map1[@@iterator]()`
Returns a new Iterator object that contains a two-member array of `[key, value]` for each element in the `Map` object in insertion order.

#### WeakMaps

- Can only use objects as keys.
- Keys must be objects, and not primitive values. This allows for better memory management in certain scenarios.
- Is not iterable.
- Does not provide any methods to iterate over the keys, values, or entries. This is because the keys can be garbage collected at any time, making iteration over them unreliable.
#### Sets

Collections of unique values.  A value in a `Set` may only occur once; it is unique in the `Set`'s collection.
```js
const mySet = new Set();
mySet.add(1);
mySet.add("some text");
mySet.add("foo");

mySet.has(1); // true
mySet.delete("foo");
mySet.size; // 2

for (const item of mySet) {
  console.log(item);
}
// 1
// "some text"

```
#### WeakSets

- Can only store objects.
- Cannot store primitive values like numbers, strings, or booleans.

### JSON - (**J**ava**S**cript **O**bject **N**otation) 

#### Full JSON grammar
```JSON
JSON-text = object / array
begin-array     = ws %x5B ws  ; [ left square bracket
begin-object    = ws %x7B ws  ; { left curly bracket
end-array       = ws %x5D ws  ; ] right square bracket
end-object      = ws %x7D ws  ; } right curly bracket
name-separator  = ws %x3A ws  ; : colon
value-separator = ws %x2C ws  ; , comma
ws = *(
     %x20 /              ; Space
     %x09 /              ; Horizontal tab
     %x0A /              ; Line feed or New line
     %x0D                ; Carriage return
     )
value = false / null / true / object / array / number / string
false = %x66.61.6c.73.65   ; false
null  = %x6e.75.6c.6c      ; null
true  = %x74.72.75.65      ; true
object = begin-object [ member *( value-separator member ) ]
         end-object
member = string name-separator value
array = begin-array [ value *( value-separator value ) ] end-array
number = [ minus ] int [ frac ] [ exp ]
decimal-point = %x2E       ; .
digit1-9 = %x31-39         ; 1-9
e = %x65 / %x45            ; e E
exp = e [ minus / plus ] 1*DIGIT
frac = decimal-point 1*DIGIT
int = zero / ( digit1-9 *DIGIT )
minus = %x2D               ; -
plus = %x2B                ; +
zero = %x30                ; 0
string = quotation-mark *char quotation-mark
char = unescaped /
    escape (
        %x22 /          ; "    quotation mark  U+0022
        %x5C /          ; \    reverse solidus U+005C
        %x2F /          ; /    solidus         U+002F
        %x62 /          ; b    backspace       U+0008
        %x66 /          ; f    form feed       U+000C
        %x6E /          ; n    line feed       U+000A
        %x72 /          ; r    carriage return U+000D
        %x74 /          ; t    tab             U+0009
        %x75 4HEXDIG )  ; uXXXX                U+XXXX
escape = %x5C              ; \
quotation-mark = %x22      ; "
unescaped = %x20-21 / %x23-5B / %x5D-10FFFF
HEXDIG = DIGIT / %x41-46 / %x61-66   ; 0-9, A-F, or a-f
       ; HEXDIG equivalent to HEXDIG rule in [RFC5234]
DIGIT = %x30-39            ; 0-9
      ; DIGIT equivalent to DIGIT rule in [RFC5234]
```

### Stack

There's more than one way to implement a stack, but probably the simplest is using **an array with its push and pop methods**.
```js
// We create a class for each node within the stack
class Node {
    // Each node has two properties, its value and a pointer that indicates the node that follows
    constructor(value){
        this.value = value
        this.next = null
    }
}

// We create a class for the stack
class Stack {
    // The stack has three properties, the first node, the last node and the stack size
    constructor(){
        this.first = null
        this.last = null
        this.size = 0
    }
    // The push method receives a value and adds it to the "top" of the stack
    push(val){
        var newNode = new Node(val)
        if(!this.first){
            this.first = newNode
            this.last = newNode
        } else {
            var temp = this.first
            this.first = newNode
            this.first.next = temp
        }
        return ++this.size
    }
    // The pop method eliminates the element at the "top" of the stack and returns its value
    pop(){
        if(!this.first) return null
        var temp = this.first
        if(this.first === this.last){
            this.last = null
        }
        this.first = this.first.next
        this.size--
        return temp.value
    }
}

const stck = new Stack

stck.push("value1")
stck.push("value2")
stck.push("value3")

console.log(stck.first) /* 
        Node {
        value: 'value3',
        next: Node { value: 'value2', next: Node { value: 'value1', next: null } }
        }
    */
console.log(stck.last) // Node { value: 'value1', next: null }
console.log(stck.size) // 3

stck.push("value4")
console.log(stck.pop()) // value4
```


#### Queue

Similar to stack, but based on convention First in First Out. 

```js
// We create a class for each node within the queue
class Node {
    // Each node has two properties, its value and a pointer that indicates the node that follows
    constructor(value){
        this.value = value
        this.next = null
    }
}

// We create a class for the queue
class Queue {
    // The queue has three properties, the first node, the last node and the queue size
    constructor(){
        this.first = null
        this.last = null
        this.size = 0
    }
    // The enqueue method receives a value and adds it to the "end" of the queue
    enqueue(val){
        var newNode = new Node(val)
        if(!this.first){
            this.first = newNode
            this.last = newNode
        } else {
            this.last.next = newNode
            this.last = newNode
        }
        return ++this.size
    }
    // The dequeue method eliminates the element at the "beginning" of the queue and returns its value
    dequeue(){
        if(!this.first) return null

        var temp = this.first
        if(this.first === this.last) {
            this.last = null
        }
        this.first = this.first.next
        this.size--
        return temp.value
    }
}

const quickQueue = new Queue

quickQueue.enqueue("value1")
quickQueue.enqueue("value2")
quickQueue.enqueue("value3")

console.log(quickQueue.first) /* 
        Node {
            value: 'value1',
            next: Node { value: 'value2', next: Node { value: 'value3', next: null } }
        }
    */
console.log(quickQueue.last) // Node { value: 'value3, next: null }
console.log(quickQueue.size) // 3

quickQueue.enqueue("value4")
console.log(quickQueue.dequeue()) // value1
```


#### Linked list & doubly linked list

**Linked lists** are a type of data structure that store values in the form of a **list**. Within the list, each value is considered a **node**, and each node is connected with the following value in the list (or null in case the element is the last in the list) through a **pointer**.

There are two kinds of linked lists, **singly linked lists** and **doubly linked lists.** Both work very similarly, but the difference is in singly linked lists each node has a **single pointer** that indicates the **next node** on the list. While in doubly linked lists, each node has **two pointers**, one pointing to the **next node** and another pointing to the **previous node**.

in doubly linked list he first element of the list is considered the **head**, and the last element is considered the **tail**. Like with arrays, the **length** property is defined as the number of elements the list contains.