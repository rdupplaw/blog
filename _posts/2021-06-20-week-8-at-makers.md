---
title: "Week 8 at Makers"
date: 2021-06-20
tag: makers diary
---

This week we started our second group engineering project, making a simplified Facebook clone in Ruby on Rails. The goal of this project is to learn to build production-quality software as part of a team. This means writing tested, readable code that follows good design principles like the single responsibility principle, but it also means working well with other developers to plan, design and produce software, with each developer contributing to the team.

None of us had used Rails before, so for the first day and a half we did some individual learning. I feel I learn best with written resources, so I stuck to the official [_Ruby on Rails Guides_](https://guides.rubyonrails.org/index.html) and [_The Ruby on Rails Tutorial_](https://www.railstutorial.org/book) by Michael Hartl. The [_Getting Started with Rails_](https://guides.rubyonrails.org/getting_started.html) guide covered pretty much everything I needed to start working with Rails (routes, controllers and actions, models, views, generators), and I consulted the other guides for specifics when working on a particular area. Michael Hartl's tutorial was especially helpful for showing test-driven development in Rails, though I had to translate Minitest to RSpec.

After lunch on Tuesday we all felt ready to start working with Rails. We had a planning session where we identified the 6-8 most important user stories, estimated their complexity then distributed them between each pair.

The first task for my pair was to order the posts by descending date i.e. latest posts first. Checking the documentation we found that the Active Record Query Interface supports this with the `#order` method. `Post.order(created_at: :desc)` gave us all posts in descending order of date created.

We also configured Continuous Integration/Continuous Deployment with CircleCI and Heroku. CircleCI runs RSpec on pull requests and on every push to the main branch. If RSpec passes, CircleCI will deploy the code to Heroku. This workflow means we can quickly identify problems in pull requests without having to pull and test the code on our own workstations. It also means that new features merged into the main branch are automatically available on our website, as long as they pass all tests.

We now have a week off from Makers and I'm going to take some time to relax. We have an individual challenge to create a clone of Instagram, which I'll start working on towards the end of the week. For our Facebook clone I wrote the sign up and login code from scratch following Michael Hartl's book, so for Instagram I'm going to try out the [Devise gem](https://github.com/heartcombo/devise). I also want to look at [Bootstrap](https://getbootstrap.com/), and CSS in general, to add some styling and responsive design to my app.