---
title: "Day 6 of 30 - Ruby Coding Challenge - Factorial Numbers Ugly Version"
date: 2020-06-14T13:49:23+06:00
draft: false

# post thumb
image: "images/post/ruby/ruby-series/day-6-of-30-Ruby-Coding-Challenge-factorial-number-version-1.png"

# meta description
description: "Day 6 of 30 - Ruby Coding Challenges in 30 Days. We're going to explore how to calculate Factorial Numbers in Ruby. This will be the ugly version that will be refactored later"

# taxonomies
categories: 
  - "Ruby"
tags:
  - "Ruby Series"
  - "30DaysCoding"

# post type
type: "post"
---

Hey folks!

In today's post, which is the writing version of the [Youtube video](https://www.youtube.com/watch?v=Ee1p3P-Yx_c), we'll explore how to calculate Factorial Numbers in Ruby.
I know that you have heard about that before, but just a refresh:

## Fancy Factorial definition

> The factorial of a number N is the product of all positive integers less then or equal to N

We indicate a factorial with an exclamation mark, 5! for example

Real life:

> Factorial of 5! is 5*4*3*2*1=120

which gives us the following pattern

> Factorial of 5! is 5*(5-1)*(5-2)*(5-3)*(5-4)

a little bit more generic:

> Factorial of N! is N*(N-1)*(N-2)**...**1

Great! We're on the same page

It's time to code!

## Algorithm Version 1. As usual, Ugly.

As usual, we'll take the following steps:

- problem definition
- first algorithm version to get the job done, which usually is ugly
- later, we'll refactor the code a little bit more
- then, we'll create the final version, which should have a decent code design :)

```ruby
def factorial(number)
  result = number
  while number > 1
    result = result * (number - 1)
    number = number - 1
  end
  return result
end

puts factorial(5) # 120
```

The code is pretty simple

- we receive a number N (let's say 5)
- we create a while loop, going from 5 to 1
- for each iteration we decrement the argument **number** until it reaches 1
- for each iteration we multiply the previous result with the current **number - 1**, following the Factorial pattern

**Why does this code is not that great?**

- we're mutating (fancy word for changing) the argument **number**
- we have to control the loop by ourselves, which is not that readable
- it's too complex for something that should be simpler

However, the goal was reached! It gets the job done.

In the next video, we'll explore a version a lit bit more readable, therefore, more maintainable and beautiful :)

{{< youtube Ee1p3P-Yx_c >}}

Don't forget to keep in touch and say hi Alex

[Twitter](https://twitter.com/_alex_gama/)
[Youtube](https://www.youtube.com/channel/UCn09BXJXOCPLARsqNvxEFuw?view_as=subscriber/)
[Instagram](https://www.instagram.com/_alex_gama)
[Linkedin](https://www.linkedin.com/in/alexandregama/)
[GitHub](https://github.com/alexandregama)