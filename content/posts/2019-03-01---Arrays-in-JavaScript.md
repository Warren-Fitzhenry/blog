---
title: Arrays in JavaScript
date: "2019-03-01T22:40:32.169Z"
template: "post"
draft: false
slug: "Arrays in JavaScript"
category: "JavaScript"
tags:
  - "JavaScript"
  - "Web Development"
description: "A brief synopsis of arrays in JavaScript."
socialImage: "/media/42-line-bible.jpg"
---

JavaScript’s latest version (ES6) has introduced a number of new Array prototype methods. Over the next few blog posts I’ll go over the most useful of these in detail, including how each of them operate under-the-hood in order to fully understand how they work.

But first off we should understand what an array in JavaScript is. An array in JavaScript is an object. For example, we can create an array using an array literal:

`const cricketers = ['amla', 'de villiers', 'smith', 'kohli'];`

In our array, the first value will get the property name 0, and the second 1, and so on, allowing us to retrieve value from the array as follows:

`cricketers[1];   // 'de villiers'`

We can produce a very similar result by creating a new object literal:

```javascript
const cricketersObject = {
    '0': 'amla',
    '1': 'de villiers',
    '2': 'smith',
    '3': 'kohli',
}
```

Both cricketers and cricketersObject are objects, and both have exactly the same property names and values. However, cricketers inherits from the Array.prototype, whereas cricketersObject inherits from the Object.prototype.

JavaScript arrays can contain elements of any value type, including nested arrays and objects:

```javascript
const assortedArray = [
    apple', 
    '0.5', 
    ['nested', 'array'],
    {'name': 'nested'},
    true,
    false,
    null,
    undefined
];
```
## Array.length

The Array.length of an array is the largest integer property name in the array plus one, for example:

`assortedArray.length // 8`

The length property can be set explicitly – setting it to less than the current number will delete those with a property name larger than the new length:

```javascript
assortedArray.length = 2;
// assortedArray becomes ['apple', '0.5']
```

We can also append items to the end of an array by using:

```javascript
assortedArray[assortedArray.length] = 'pineapple';
// assortedArray becomes ['apple', '0.5', 'pineapple']
```

However, we can rather use Array.push method to append items to the end of an array.

Deleting elements
We can use the delete operator on an array to remove elements, but that leaves a hole in the array, as all elements to the right of the deleted item will retain their property names:

```javascript
delete assortedArray[0];
// assortedArray becomes [ undefined, '0.5', 'pineapple'
```

## When to use an array instead of object?
There is a simple rule for this: if your property names are small sequential integers, use an array. Otherwise, use an object.