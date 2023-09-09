---
title: "Week 2 at Makers"
date: 2021-05-09
tag: makers diary
---

## Code review

At the start of my sixth week at Makers, my second week of the course proper, we paired to review the weekend challenge. My pair and I exchanged helpful feedback on each other's code. His feedback for me was to adhere more closely to the maxim of test-driven development: Red-Green-Refactor-Commit. I had written and committed tests and code in chunks. Instead of focussing on one test and thus one problem, I had tried to solve several problems at once. 

This makes mistakes more likely (with both the test logic and the code logic), and it undermines the iterative approach of TDD. By writing several tests up front, I was making more or less far-reaching decisions about the implementation of future functionality before I needed that functionality. If the commit caused a bug, identifying which change produced it would be time-consuming; if I committed functionality incrementally, it would be trivial.

In this week's challenge, I committed much more frequently.

In terms of giving feedback, I learned two useful frameworks. The first is ASK: Actionable, Specific and Kind. Ideally feedback should be practicable, should precisely identify the problem, and should be done in good faith. It never hurts to complement before you criticise.

Another framework is Observation -> Feeling -> Needs -> Request. Start with something concrete you've observed, then how that makes you feel. Explain your needs and what you request from the other person.

## Object-Oriented Programming: Polymorphism, duck typing, inheritance, composition, dependency injection and delegation

Polymorphism means 'many forms' and refers to how many different objects can respond to the same message (i.e. the same method). As each object can have it's own version of this message, the message has many forms. In other words, a single interface is implemented on many different classes. This can be achieved by duck typing, inheritance and composition.

Duck typing: "If it walks like a duck and it quacks like a duck, then it must be a duck". A single method (or several methods) can be implemented on multiple different classes, creating a conceptual duck type. The example used by Sandi Metz in *Practical Object-Oriented Design* involves a trip object asking other objects to prepare for a trip. A mechanic needs to prepare bikes, a trip coordinator needs to buy food, and a driver needs to get the coach ready. Instead of the trip object having to know all this about the mechanic, coordinator and driver, a conceptual duck type 'preparer' is created, with each of the preparers having a prepare\_trip method. So when the trip tells the mechanic to prepare the trip, the mechanic gathers the bicycles and prepares them all; when the driver is told to prepare the trip, they get the coach ready, and so on.

Inheritance is when one class is a derivative of another, with the subclass sharing all the methods of the superclass, but being able to add to or overwrite the superclass' methods. If you call a method which hasn't been defined on the subclass, Ruby will look up the inheritance chain until it finds the method, or can't find it.

With composition, you can take functionality from multiple sources into one class. Using the include keyword, you can add the methods defined in a module into your class. Another way of achieving this is to pass an instance of another class into your class, then calling the methods of that class when desired.

Dependency injection means that, instead of writing a dependency into a class (e.g. by including OtherClass.new somewhere in your Class), you pass an instance of that other class into the initialize function of your class. This means your class is no longer dependent on the name of the other class, and can be used with any class that implements the required methods.

Delegation simply means passing on a message to another object, and should be used where it makes sense for some functionality to exist within another class.

## Unified Modelling Language: Sequence and class diagrams

Sequence diagrams and class diagrams are both very helpful for thinking about and designing object-oriented programs. Sequence diagrams show the sequence of messages being sent between objects, and often help you see where you need a new class or duck type. Class diagrams help clarify where methods and attributes should be located in your application.

## RSpec mocking

For the end of unit challenge this week, we integrated our program with Twilio to send text messages. We used the Twilio Ruby API. Though this isn't too complicated in itself, we didn't want our RSpec tests to send a text every time they ran, so we had to create a double for the Twilio Ruby client.

To send a text with the Twilio API, you have to run Client.messages.create(message\_info). I created a double for the Client (which I passed to my own class through dependency injection). I made this double respond to .messages with another double, which then responded to .create with another double which mimicked the API response (an object with an error\_code of nil):

```
let(:message_response_double) { double(:response, error_code: nil) }
let(:message_double) { double(:message, create: message_response_double) }
let(:text_message_client_double) { double(:client, messages: message_double) }
```