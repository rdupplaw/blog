---
title: "Week 10 at Makers"
date: 2021-07-11
tag: makers diary
---

This week we were assigned individual challenges meant to simulate tech tests from prospective employers. The goal of these challenges was to solve a technical problem with well-crafted code. This means following a test-driven development process and writing readable, changeable, well-designed, object-oriented code. This tests every technical skill we've learnt over the course so far.

The first challenge was to write an application to simulate a simple bank account, with deposits, withdrawals and statements. My solution is [here](https://github.com/rdupplaw/bank-tech-test). 

I used Ruby and RSpec. I designed three classes: `BankAccount`, responsible for holding transactions; `BankTransaction`, responsible for holding the information relating to a single transaction; and `BankAccountStatementGenerator`, responsible for formatting transactions as a bank statement. There is more explanation of my design decisions in the readme.

As the feedback from our coach was broadly positive, I moved onto the next challenge: the Gilded Rose kata. This is a fairly well-known kata, designed to practice dealing with a legacy codebase. The kata was originally written in C#, but I used a JavaScript version. My solution is [here](https://github.com/rdupplaw/gilded-rose-js-jest).

I began by writing unit tests for each class, and then writing an integration test (the kata came with a test using TextTest, which I more-or-less translated into Jest). Once I was happy that I'd covered core, edge and invalid cases in my tests, I could refactor with some confidence that I wasn't breaking everything.

I refactored the logic of the application into several methods, each with a single responsibility. I also simplified the logic as far as possible, and where I saw shared logic or repetition I refactored into a singly-responsible method.

The key part of this challenge is the requirement to add a 'conjured' item feature. This is what mandates the refactoring (the original code is too complex to change with confidence), and the refactoring mandates testing. 

With the refactoring completed, adding the new feature was simple. I just needed to add a new condition to an existing `if`/`else` statement to check for conjured items, and then call an existing method with the right arguments. In this case, it looked like this:

```
// from line 10 of shop.js
if (this._isConjured(item)) {
        this._updateItem(item, -2)
// rest of if/else statement
```

If I had free reign, I think I would have used inheritance and polymorphism to solve this kata. It could make sense to have a base `Item` class with an `updateQuality` method, from which more specific `AgedBrie` or `Sulfuras` classes could inherit, each with a specialised `updateQuality` method. However in this kata, you're not allowed to change the `Item` class.