---
title: "Day 15 of 30 - Ruby Coding Challenge - Fibonacci Sequence Recursively"
date: 2020-06-26T13:49:23+06:00
draft: false

# post thumb
image: "images/post/ruby/ruby-series/day-15-of-30-Ruby-Coding-Challenge-fibonacci-sequence-recursively.png"

# meta description
description: "Day 15 of 30 - Ruby Coding Challenges in 30 Days. We're going to solve the famous Fibonacci sequence recursively in Ruby. This is not a better strategy than the previous one, this will be just another option :)"

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

This is the blog post version of the [Youtube video](https://youtu.be/eFBBSQvBLJE) from the [30 Ruby Coding Challenges in 30 Days series](https://courses.alexgama.io/course?courseid=ruby-coding-challenges-course)

Today we'll solve the [previous Fibonacci problem](https://youtu.be/2zMUGAD6s6A) using the dreaded recursion approach

A little bit of theory [was explored in this video](https://youtu.be/jQUlFVqyJxQ) and today I'll straight to the point

## Fibonacci Recursively in Theory

Just to remember:

- A recursive method is a method that calls itself
- A recursive method usually solves a smallest version of the bigger (original) problem

When it comes to Fibonacci, the definition already gives us a hint of how to solve it recursively:

> To get the next number in a sequence, you have to sum the previous two numbers

Let's say that we want the first 8 numbers in the Fibonacci sequence:

```ruby
0 1 1 2 3 5 8 13
```

Notice that to get the value 13:

- we need to first calculate the first 7 numbers of a Fibonacci sequence

But to get the value 8:

- we need to first calculate the first 6 numbers of a Fibonacci sequence

But to get the value 5:

- we need to first calculate the first 5 numbers of a Fibonacci sequence

Yup, you got it : )
We need to calculate the Fibonacci number of the previous 2 numbers

## Fibonacci Recursively in Ruby

**Version 1**

Notice that the **count** argument controls when to stop the method calling itself

```ruby
def fibonacci(count)
  if count <= 1
    count
  else
    fibonacci(count - 1) + fibonacci(count - 2)
  end
end
```

**Version 2**

In 1 line, we could use a ternary operation:

```ruby
def fibonacci(count)
  count <= 1 ? count : fibonacci(count - 1) + fibonacci(count - 2)
end

puts fibonacci(8)
# 0 1 1 2 3 5 8 13 21
```

Great! 

Probably you may already know that this approach doesn't have a good performance but this is something for another post :)

Thanks for the visit and see you in the next coding challenge!

{{< youtube eFBBSQvBLJE >}}

Don't forget to come by and say hi Alex

[Courses](https://courses.alexgama.io/)
[Twitter](https://twitter.com/_alex_gama/)
[Youtube](https://www.youtube.com/c/AlexandreGamaLima)
[Instagram](https://www.instagram.com/_alex_gama)
[Linkedin](https://www.linkedin.com/in/alexandregama/)
[GitHub](https://github.com/alexandregama)