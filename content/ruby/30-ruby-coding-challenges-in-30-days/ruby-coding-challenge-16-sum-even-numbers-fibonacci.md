---
title: "Day 16 of 30 - Ruby Coding Challenge - Sum Even Numbers in a Fibonacci Sequence"
date: 2020-06-28T13:49:23+06:00
draft: false

# post thumb
image: "images/post/ruby/ruby-series/day-16-of-30-Ruby-Coding-Challenge-sum-even-numbers-fibonacci-sequence.png"

# meta description
description: "Day 16 of 30 - Ruby Coding Challenges in 30 Days. We're going to sum all the even numbers in a given Fibonacci sequence"

# taxonomies
categories: 
  - "Ruby"
tags:
  - "Ruby Series"
  - "30DaysCoding"

# post type
type: "post"
---

Hey friends!

This is the blog post version of the [Youtube video](https://youtu.be/hs4cVsva5x4) from the [30 Ruby Coding Challenges in 30 Days series](https://courses.alexgama.io/course?courseid=ruby-coding-challenges-course)

We've solved the Fibonacci sequence [here](https://youtu.be/rccOdzwtOD0), [here](https://youtu.be/2zMUGAD6s6A) and [here](https://youtu.be/eFBBSQvBLJE), which means that we have some clues of how to create a Fibonacci sequence :)

Today we want to be a little bit daring by solving the following problem:

> I want to sum all even numbers in a Fibonacci sequence

## Fibonacci Sequence in Ruby

As you already know, this is one of the solutions:

```ruby
def fibonacci_sum(count)
	number = 0
  sequence = []
  (0..count).each do |item|
    number = item if item <= 1
    number = sequence[-1] + sequence[-2] if item > 1
    sequence << number
  end
	sequence
end
```

We're returning a Fibonacci sequence, however, that's not what we're looking for

## Sum Even Numbers in a Fibonacci Sequence in Ruby

We're going to:

- add a local variable called **sum**
- then update this variable **only if the number is even**
- return the **sum** variable

```ruby
def fibonacci_sum(count)
  sum = 0
	number = 0
  sequence = []
  (0..count).each do |item|
    number = item if item <= 1
    number = sequence[-1] + sequence[-2] if item > 1
    sequence << number

    sum += number if number % 2 == 0
  end
  sum
end
```

Math comes handy here. An even number is a number dividable by 2, which in Ruby is represented by

```ruby
number % 2 == 0
```

Quite simple, isn't it? 😬

[In the next video](https://youtu.be/86lEtgO4yTM), we're going to explore a decent and beautiful Ruby Way to solve this same problem, see you there :)

Thanks for the visit and see you in the next coding challenge!

{{< youtube eFBBSQvBLJE >}}

Don't forget to come by and say hi Alex

[Courses](https://courses.alexgama.io/)
[Twitter](https://twitter.com/_alex_gama/)
[Youtube](https://www.youtube.com/c/AlexandreGamaLima)
[Instagram](https://www.instagram.com/_alex_gama)
[Linkedin](https://www.linkedin.com/in/alexandregama/)
[GitHub](https://github.com/alexandregama)