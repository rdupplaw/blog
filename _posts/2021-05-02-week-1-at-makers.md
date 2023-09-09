---
title: "Week 1 at Makers"
date: 2021-05-02
tag: makers diary
---

This week I started the course proper at Makers.

I really enjoyed this week. I met my cohort all together for the first time, and worked with several of them on the pair programming challenge over the course of the week.

In workshops, we learnt about test-driven development (TDD), object-oriented programming (OOP) and debugging. This built upon what we learnt in the pre-course, and we applied everything we had learnt to the pair programming challenge and the end of unit challenge for the week.

## Self-directed learning

Self-directed learning is strongly emphasised at Makers. While they provide guidance, resources and challenges, it's our responsibility to think about our learning goals, how to get there and how to evaluate our progress. This is intended to be similar to the work of junior developers, who spend much of their time self-learning new concepts and information.

Makers gives us broad goals for the course (e.g. "I can create any program with TDD") and for each week (e.g. "I can test-drive a simple program"), but on a day-to-day basis we decide which of these weekly and course goals we need to work on, devise daily goals, find learning resources and evaluate our progress. In this way, we lead our own learning. Makers, and our coaches, are here to guide us through this process and teach us to teach ourselves.

This doesn't mean we learn alone though. As a cohort we share knowledge and help each other, and we can get feedback from coaches on areas to improve.

For example, this week I decided that I wanted to improve my knowledge of OOP and TDD. For OOP, I researched some OO principles like encapsulation and cohesion, then undertook a practical coding challenge from the Makers curriculum. For TDD, I read a series of RSpec tutorials I found on the web, then applied this to the end of unit challenge. Next week I'll get this work reviewed by a coach to help me evaluate my progress and see where I need to improve, which will stimulate my next round of self-directed learning.

To keep track of all this, I keep a daily journal in a note-taking application. At the end of the week, I reread the entries and reflect, then write this blog. I also use a kanban board application to keep track of the projects, challenges and resources I want to complete.

## Emotional intelligence

Emotional intelligence (EI) also plays a prominent part in the Makers curriculum. This week I joined the daily meditation sessions where we were introduced to the concepts of EI. One key concept is self-awareness, which comprises emotional awareness, accurate self-assessment and confidence. 

Emotional awareness means being able to identify and in some sense distance yourself from your feelings, so that they don't exert too much influence over your actions. One way of doing this is affect labelling: putting your feelings into words, which often reduces the effect the feelings have on you.

Accurate self-assessment is about honestly identifying your strengths and weakness: not being too hard on yourself and not being too self-assured. Key to this is feedback from your seniors and colleagues.

When you're emotionally aware and can accurately assess yourself, you will be confident in your ability. You'll know whether you can achieve something by yourself or when to ask for help, you'll be able to track your emotions and take care of yourself, and you'll always be improving.

## TDD

The basic concept of unit testing is Arrange-Act-Assert: arrange the objects you're testing, act on them, then assert what should be the result. For example:

```
input = 'abc'
result = input.reverse
expect(result).to eq('cba')
```

The first line arranges the initial object, a string. The second line acts upon the string. The last line uses methods from RSpec, a Ruby testing framework, to assert that we expect the result to equal 'cba', the reverse of 'abc'.

## Debugging

The simplest way of debugging a program in Ruby is to use `p` statements to show you the value of an expression at a certain point in the program's execution. 

When you're debugging a program it's generally because it's giving you an output you don't expect or want, meaning somewhere in your program there's a bug. To find it, you can use `p` statements at various points, and by systematically moving them around the program you can find the line at which your bug occurs. 

This is known as tightening the loop, because you're essentially moving `p` statements closer and closer together until there is only a line between them, isolating the bug to this line.