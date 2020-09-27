---
title: Implementation of a stack in JavaScript
date: "2019-07-01T22:40:32.169Z"
template: "post"
draft: false
slug: "Implementation of a stack in JavaScript"
category: "JavaScript"
tags:
  - "JavaScript"
  - "Web Development"
description: "Find out how to implement this common data structure in JavaScript."
socialImage: "/media/42-line-bible.jpg"
---

The Stack data structure is very useful and has many applications. The basic design if that of a linear data structure in which the addition or removal of elements follows the FILO order (first in, last out).

Let’s create a skeleton of a stack class which contains a constructor in which we declare an array to implement our stack.

```javascript
// Stack class
class Stack {
    // We are using an Array to implement our stack
    constructor() {
    this.items = [];
}
    // Functions to be implemented
    // push(item)
    // pop()
    // peek()
    // isEmpty()
}
```

We’ve added some methods on our stack class which we would need to implement, allowing us to add items to the stack (push), take an item off our stack (pop), check the last value of the stack (peek), and check whether the stack is empty (isEmpty).

Let’s add these in.

### `Push(value)` – this adds an element to the stack. The push methods has a parameter which is the value of the item we want to add to the stack.

```javascript
// push function
push(value) {
    // push element into the items
    this.items.push(value);
}
```

### `Pop()` – removes an element from the stack, also returning an error if stack is empty

```javascript
// pop function
pop() {
    // return top most element in the stack
    // and removes it from the stack
    if(this.items.length == 0) return "Stack is empty";
    return this.items.pop();
}
```

### `Peek()` – returns the top most element in the stack (doesn’t delete it)

```javascript
// peek function
peek() {
    // return the top most element from the stack
    // but doesn't delete it
    return this.items[this.items.length - 1];
}
```

### `isEmpty()` – return true if the stack is empty

```javascript
// isEmpty function
isEmpty() {
    // return true if stack is empty
    return this.items.length === 0;
}
```

Let’s run through a quick example of how the we can use our new Stack class.

```javascript
// Adding element to the stack
stack.push(10);
stack.push(20);
stack.push(30);

// Printing the stack element
// prints [10, 20, 30]
console.log(stack.printStack());

// returns 30
console.log(stack.peek());

// returns 30 and remove it from stack
console.log(stack.pop());

// returns [10, 20]
console.log(stack.printStack());
```