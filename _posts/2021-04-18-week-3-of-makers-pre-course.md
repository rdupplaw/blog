---
title: "Week 3 of Makers pre-course"
date: 2021-04-18
tag: makers diary
---

This week we were introduced to two major concepts: pair programming and test-driven development.

## Pair programming

Pair programming is essentially one programmer helping another programmer (when there are more than two people, it's called mob programming or ensemble programming). Each person takes turns "driving" (i.e. directly writing code) while the other person "navigates" (i.e. takes a back seat, thinks about the bigger picture, offers suggestions and looks at documentation). You switch between these roles quite frequently, about once every fifteen minutes.

There are a few significant benefits of this. With two people, each can hold the other accountable for writing tests and staying focussed where a lone programmer might cut corners. The navigator might also be in a better position to think about edge cases and possible bugs that new code would introduce. The architecture and general quality of the program should also be better with two people putting their heads together.

Even though we are working remotely, we can still pair quite easily. With a shared GitHub repo, the driver can share their screen over Zoom/Slack while they write, and then push their changes to GitHub. When they switch roles, the former navigator can pull the changes and pick up where their partner left off.

I tried pair programming with some people in my course cohort this week. We started with mob programming, where four of us collaborated on a simple program. "Mobbing" instead of pairing reduced the tension for our first time. Once I was more comfortable, I tried pairing. There is definitely a perceptible, positive pressure from working as a pair. You don't want to let the other person down, and you don't want to cut any corners because your pair will hold you to account, and vice versa. This might sound stressful, but it's actually quite fun. On top of the positive impact on programming, there is also knowledge-sharing. You might learn a helpful switch for a command-line program, or a piece of syntax which can simplify your code.

## Test-driven development

Test-driven development (TDD) is a programming workflow where you write tests according to the specification for your program, then write code to satisfy those tests (then refactor that code to clean it up). This can be summarised as Red-Green-Refactor:

Red: Write a test which describes something you want your program to do. You should check that this test fails: if it passes, you have either (1) written the test incorrectly or (2) the functionality already exists in your program and new code isn't needed.

Green: Write the simplest possible code that satisfies your test.

Refactor: Refactor your code to improve readability and maintainability without changing any functionality. Check that your tests are still passing after each refactor.

Working in this way results in fewer bugs in the end product. It also forces you to think about exactly what your program needs to do before you start writing any code. The workflow encourages you to write more modular code which can be independently tested and reused (this links with what I've been reading in _Practical Object-Oriented Design: An Agile Primer with Ruby_ about loosely coupling classes so that they are more reusable).