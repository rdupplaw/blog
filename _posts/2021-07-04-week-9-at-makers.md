---
title: "Week 9 at Makers"
date: 2021-07-04
tag: makers diary
---

## Review

We had last week off, so I booked a review. This involves an external examiner acting as a technical customer with requirements for a piece of software. You start by gathering information from the customer and defining the specification, then you implement the program using TDD. The examiner observes and at the end gives feedback on your process. You also receive a written report containing feedback relating to the Makers course goals.

This was my second review, and it went much better than the first one. I had fixed all the problems that were identified last time, so now I'm graded as 'steady' or 'strong' on every goal (I was graded 'improving' on several on my first review). I only had one real problem this time:  I wrote slightly _too many_ tests (i.e. tests for logic that has already been implemented, which doesn't provide value to the customer).

## Engineering Project

This week we completed our second group engineering project, a simplified clone of Facebook. I was worried it would be difficult to start back up again after our week off, but we worked well from the first day. 

We improved our process by assigning a leader for each day, who leads the standup and retro as well as assigning specific people to review each pull request. This meant pull requests were reviewed and features shipped much more quickly, especially with continuous deployment to Heroku through CircleCI.

However, towards the end of the week, the work became a bit tedious. I think there were a combination of reasons for this. One is that we changed focus from big features to smaller refinements and bugfixes. It just isn't as fun or satisfying to change the navbar slightly or fix a rare bug as it is to implement a news feed or profile page.

Another reason for the tedium was that last week we hadn't been focussing hard enough on clean, readable code and good object-oriented design, which made it harder to change the code later on.

One more problem was that our tests had a lot of hardcoded values where we should have used variables, helper functions or `let`/`before` blocks, so that there was less repetition. If we wanted to change something towards the end of our project, it would probably take longer to fix all the broken tests than to actually implement the new feature.

If we had followed good object-oriented design principles, like the single responsiblity principle and _Don't repeat yourself_, and aggressively refactored as we went along, it would have been easier to change or add features towards the end of the project.