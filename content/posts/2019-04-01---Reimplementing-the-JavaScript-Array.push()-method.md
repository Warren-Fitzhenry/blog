---
title: Reimplementing the JavaScript Array.push() method
date: "2019-04-01T22:40:32.169Z"
template: "post"
draft: false
slug: "Reimplementing the JavaScript Array.push() method"
category: "JavaScript"
tags:
  - "JavaScript"
  - "Web Development"
description: "Find out more on how the JavaScript arrays work under the hood by implementing this common array method."
socialImage: "/media/42-line-bible.jpg"
---

Adding elements to an array is a very common practice when using JavaScript, made easy by the push() method:

```javascript
const newArray = ['senna', 'prost'];
newArray.push('hill');
// newArray becomes ['senna', 'prost', 'hill']
```

### Let’s try and reimplement a simple version of what the Array.push() method is doing under-the-hood.

In a previous post, we learnt that every JavaScript array has a length property:

`newArray.length;  // 3`

The `Array.length` property of an array is the largest integer property name in the array plus one. Remember, the property name refers to the ‘key’ of an element, not the value. The above array is not dissimilar to this object:

```javascript
const newArrayObject = { 
  '0':'senna',
  '1': 'prost', 
  '2': 'hill'
  };
```

We also learnt that we can add an element to the end of array by utilising this length property:

```
newArray[newArray.length] = 'schumacher';
// newArray becomes
// ['senna', 'prost', 'hill', 'schumacher']
```

Given that methods are functions attached to the array prototype object, here is an example of how we could create our our own array object with a push method using our knowledge of the `Array.length` property:

```javascript
newArray = {
    length: 0,
    push: function (value) {
      // Place the new value into the
      // next available integer key
      this[this.length] = value;

      // Update the length property
      this.length = this.length + 1;

      // Return the updated length
      return this.length;
    }
};

newArray.push('woods');
newArray.push('mickelson');

newArray[0] //  'woods'
newArray[1] //  'mickleson'
newArray.length // 2
```