---
title: A closer look at the forEach() JavaScript array method
date: "2019-05-01T22:40:32.169Z"
template: "post"
draft: false
slug: "A closer look at the forEach() JavaScript array method"
category: "JavaScript"
tags:
  - "JavaScript"
  - "Web Development"
description: "Find out how the forEach() method can be used to quickly iterate of arrays."
socialImage: "/media/42-line-bible.jpg"
---

Before the `Array.forEach()` method, iterating through an array in JavaScript would involve using a for loop.

```javascript
const beans = ['kidney', 'baked', 'black'];

for (let i = 0; i < beans.length; i++) {
  console.log(beans[i]);
}

// kidney
// baked
// black
```

Using `Array.forEach()` makes things a bit simpler.

```javascript
beans.forEach((bean) => {
  console.log(bean);
})

// kidney
// baked
// black
```

### But what does the Array.forEach() method actually do?

All array methods are functions attached to the `Array.prototype` object. We want our method to execute a provided function to each element of the array. What would this method look like then? Under-the-hood, the method is still in fact using a for loop.

```javascript
Array.prototype.forEach = function (callback) {
  if (callback && typeof callback === 'function') {
    for (var i = 0; i < this.length; i++) {
      callback(this[i], i, this);
    }
  }
};
```

The for loop will iterate through each item in the array, and pass in the current item in the loop, the current index, and the array itself as arguments to the callback provided. Because the method is attached to the prototype, it can use this to refer to the array itself.

These three parameters are then passed to the callback to be used if necessary.

```javascript
beans.forEach((bean, index, array) => {
    console.log(`${index}: ${bean}`);
});

// 0: kidney
// 1: baked
// 2: black
```