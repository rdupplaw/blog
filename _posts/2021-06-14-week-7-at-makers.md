---
title: "Week 7 at Makers"
date: 2021-06-14
tag: makers diary
---

This week we were tasked with building a single-page app (SPA) in JavaScript, HTML and CSS, using no external libraries. The app allows the user to write notes, see a list of their notes, and click a single note to see the whole text. [The GitHub repository is here](https://github.com/rdupplaw/notes-js). Four of us completed this as a group project during this week's afternoons, while we spent the mornings on individual learning.

## Testing Library

Although we couldn't use any external libraries, we still wanted to follow test-driven development (TDD), so we wrote a small testing library based on Jasmine. This included `describe()` and `it()` blocks to describe our tests, plus an `expect()` function along with matchers like `toBe()`, `toThrowError()`. 

```
function expect(a) {
  return {
    toBe: function(b) {
      // compare a and b
      if (a === b) {
        console.log('Pass')
      } else {
        console.log('Fail')
      }
    },
    // ... other matchers ...
  }
}
```

This function can be used to make assertions in test cases like `expect(sum(1,1)).toBe(2)`.

I also wrote a `spyOn()` function which replaces a given method with a spy method, which can be checked on later with the matcher `toHaveBeenCalledWithArguments()`.

```
function spyOn(object, method) {
  object[method] = (function() {
    let numberOfCalls = 0
    let calledWithArguments = []
    function spyFunction(...args) {
      numberOfCalls++
      calledWithArguments = args
    }
    spyFunction.getnumberOfCalls = () => {
      return numberOfCalls
    }
    spyFunction.getCallArguments = () => {
      return calledWithArguments
    }
    return spyFunction
  })()
  return object[method]
}
```

This function replaces (or creates) the given `method` on `object` with a spy function. When the spy function runs, it increments `numberOfCalls` and saves its arguments to `calledWithArguments`. This can then be checked later with the `toHaveBeenCalledWithArguments()` matcher.

## Fetch API

The Fetch API can be used to retrieve data from network APIs. We used this to "emojify" our note text. Makers provided us with an API which could take text  containing emoji short codes like :fire: and give us back the text containing the corresponding emojis.

We had to set the content type, method and body of the request, which is straightforward with Fetch:

```
fetch("https://makers-emojify.herokuapp.com/", {
      headers: {
        'Content-Type': 'application/json'
      },
      method: 'POST',
      body: JSON.stringify({text: text})
    })
    .then(//callbacks...
```

You can chain `.then(callbackFunction)` to a `fetch()` call to provide callback functions to be run when the fetch promise resolves.

## Testing Asynchronous Functions

Asynchronous functions can be difficult to test because, writing tests conventionally, your assertions might run before the asynchronous function has resolved.

This problem can be tackled by making the callback function in your `it()` block into an asynchronous function.

```
it('stores an object with the given text', async () => {
      // test setup
      await noteController.addNote('test')
      expect(noteController.notes[0].text).toBe('test')
    })
```

The `async` keyword on the first line makes this function asynchronous. The `await` keyword basically means that this asynchronous function pauses at that point, then continues once the `noteController.addNote('test')` function (which is also an asynchronous function, returning a promise) resolves. This means the assertion doesn't run until the tested function has finished.
