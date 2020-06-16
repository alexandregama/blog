---
title: "Day 8 of 30 - Ruby Coding Challenge - Factorial Numbers - Functional Version 1"
date: 2020-06-16T13:49:23+06:00
draft: false

# post thumb
image: "images/post/ruby/ruby-series/day-8-of-30-Ruby-Coding-Challenge-factorial-ruby-way-functional-programming.png"

# meta description
description: "Day 8 of 30 - Ruby Coding Challenges in 30 Days. We're going to explore how to calculate Factorial Numbers in Ruby using a more declarative approach, which is a concept borrowed from functional programming"

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

In today's post, which is the writing version of the [Youtube video](https://www.youtube.com/watch?v=ar_EvQggpjY), we'll finally achieve our dreams of writing the Factorial Algorithm in a more Ruby way. This will be very short because, well, that's the way Ruby solves things 😄

## #1 - Previous Algorithm Version

```ruby
def factorial_version_2(number)
  final_result = number
  (1..(number - 1)).each do |item|
    final_result = final_result * item
  end
  return final_result
end

puts factorial_version_2(5)
```

It's easy to understand, however, it could be simpler

## #2 - Ruby Way for Factorial Numbers

Ruby allows us to reduce a list of arrays into a single value by applying a method, which in our case will be the multiplier method

```ruby
def factorial_version_3(number)
  (1..number).reduce(:*)
end

puts factorial_version_3(5)
```

What's happening is:

- ruby iterates over the numbers, between **1** and the given **number**
- then Ruby reduces this list of numbers into a single value by applying the given method, which multiplies the numbers

Pretty straightforward and cool, isn't it?

In the next video we'll explore the final version of this algorithm, which can be frighteningly easier. See you there :)

{{< youtube ar_EvQggpjY >}}

Don't forget to keep in touch and say hi Alex

[Twitter](https://twitter.com/_alex_gama/)
[Youtube](https://www.youtube.com/channel/UCn09BXJXOCPLARsqNvxEFuw?view_as=subscriber/)
[Instagram](https://www.instagram.com/_alex_gama)
[Linkedin](https://www.linkedin.com/in/alexandregama/)
[GitHub](https://github.com/alexandregama)