---
title: Prototype inheritance in JavaScript
date: "2019-06-01T22:40:32.169Z"
template: "post"
draft: false
slug: "Prototype inheritance in JavaScript"
category: "JavaScript"
tags:
  - "JavaScript"
  - "Web Development"
description: "Prototype inheritance is key to understanding objects in JavaScript."
socialImage: "/media/42-line-bible.jpg"
---

Every object in JavaScript is linked to a prototype object from which it can inherit properties. All objects created from object literals are linked to `object.prototype`, an object that comes standard with JavaScript.

When you make a new object, you can select the object that should be its prototype. For example, using the `Object.create` method, we can specify a bond or invisible link to an existing prototype object.

```javascript
function createUser(name, score) {
  let newUser = object.create(userFunctionStore)
  newUser.name = name;
  newUser.score = score;
}

let userFunctionStore() {
  increment: function() {this.score++}
}
```

In the above simplistic example, we are creating a new object newUser, and we are specifying that it should link to the `userFunctionStore` prototype. Any new user that we create using the createUser function will therefore have a reference to all the functionality in userFunctionStore. The user will have this prototype link stored in it’s `_proto_` property.

If we add any new properties to userFunctionStore, those properties will be available immediately to objects that are based off of that prototype.

`var user1 = createUser( 'Warren', 8);`

It is important to recognise that when we write `user1.increment()`, increment is not a method on user1, but it’s `_proto_` object contains a reference to the userFunctionStore that does contain it. JavaScript will initially try to find the increment method directly on user1, and when it doesn’t find it, it will look in it’s `_proto_` object to see if it can find it there.

```javascript
function userCreator(name, score) {
  this.name = name;
  this.score = score;
{

userCreator.prototype.increment = function(){
  this.score++;
}

let User1 = new userCretaor(‘Eva’, 9);

user1.increment();
```

In the above example, we are adding functionality to the userCreator function (we can do this because all functions in JavaScript are objects). We store the increment property and function reference in the prototype object of the function.

Using the new keyword automates the above function for us. It will automatically create an empty object named this and will also automatically return this object and save it to the variable name that was declared.

This means under the hood of using the new keyword:

`this = object.create(userCreator.prototype)`

and at the bottom of the function a hidden:

`return this`

The above function can be written as:

```javascript
class user {
	Constructor (name, score){
		this.name = name;
		this.score = score,
	}
increment() {
	this.score++;
	}
}
```

The constructor will automatically be run when the class is called, and increment will also be stored in the prototype object of the new object.

Any new object created from this class will have a reference in its `_proto_` to the object user.protoype. That is to say, user1 or user2’s protoype is user.protoype, or the reference made under user1 and user2’s `_proto_` is to the user.prototype object.