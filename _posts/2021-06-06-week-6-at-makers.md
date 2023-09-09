---
title: "Week 6 at Makers"
date: 2021-06-06
tag: makers diary
---

This week we started using (front-end) JavaScript. I completed the JavaScript curriculum on freeCodeCamp before joining Makers, but there was only a small amount of object-oriented programming and no test-driven development.

It was easy to apply the principles of object-oriented design and test-driven development, learned in Ruby, to this new language. My learning process is better now; I know how to learn by reading documentation, blogs, style guides and most of all by experimentation.

## Prototypical inheritance

I learned about the prototypical inheritance model found in JavaScript, for which the class keyword, introduced in ES6, is merely syntactical sugar, not a real class implementation like Ruby. Every JavaScript object has a prototype except for null; if an object receives a message it can't answer, it will look in its prototype, and its prototype's prototype, and so on, until it either finds an object which can respond to the message, or reaches null, which is the end of the prototype chain. Any object can act as a prototype.

The below code shows a simple example. No class is required as in Ruby. You just set one object as another object's prototype. When we call .testPrototypeProperty on testObject, it looks up the prototype chain and finds the property.

```
let testObject = {}
let testPrototype = {
	testPrototypeProperty: 'Hello, Prototype!'
}
Object.setPrototypeOf(testObject, testPrototype)
testObject.testPrototypeProperty // => 'Hello, Prototype!'
```

Here's the output in the Firefox developer tools:

```
testObject
> Object {  }
    > <prototype>: Object { testPrototypeProperty: "Hello, Prototype!" }
        > testPrototypeProperty: "Hello, Prototype!"
        > <prototype>: Object { … }
```

At the bottom we can see that testObject has a \<prototype\> object with the property testPrototypeProperty. This object corresponds to testPrototype.

## Asynchronicity

Asynchronicity means things don't necessarily happen in the order you've written them. An example is the fetch method. This function makes a network request, but its return value is a promise, not the data of the network request. 

The promise can be given a callback function to run when the promise is resolved, i.e. when the network request receives a response. This is why it's called a promise: it signifies a contract to supply a value at some point in the future, which it will pass to the specified callback function. The asynchronicity comes from the fact that while the promise is waiting to be resolved, your browser will continue executing any other code it needs to.

This asynchronous behaviour is important for user interfaces on the web because if this network request was synchronous, no JavaScript would be able to run while you were waiting on the response. This could mean the user interface becomes unresponsive for hundreds of milliseconds or seconds, which is not good user experience.

## Bowling challenge

The end of unit challenge this week was to translate into JavaScript a ten pin bowling score calculator we wrote in Ruby last weekend. I took the opportunity to improve the design by moving the frame bonus logic to the Frame class. I also isolated my unit tests and added distint integration tests.

I used Node.js to write, test and lint (with ESLint) my code, meaning there were require and module.exports statements, which don't work in browser JavaScript. I chose to use esbuild to bundle my Node.js JavaScript into browser JavaScript because I had read an article about it and wanted to try it out.

[Here's the GitHub repo.](https://github.com/rdupplaw/bowling-challenge)

For test-driven development, we used Jasmine. The syntax is very similar to RSpec, and once I was used to the parentheses and curly brackets I could apply the same TDD principles I had learnt in Ruby.

This toolchain was relatively easy to learn because I could see analogues in my Ruby toolchain.

- Node Version Manager == Ruby Version Manager
- Node.js (JavaScript runtime) == Ruby runtime
- Node Package Manager == RubyGems
- ESLint == RuboCop
- Jasmine == RSpec