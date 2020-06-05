---
title: "Day 1 of 30 - Ruby Coding Challenge - Arrays and Blocks"
date: 2020-06-04T13:49:23+06:00
draft: false

# post thumb
image: "images/post/ruby/ruby-series/30-Ruby-Coding-Challenges-Thumbnail.png"

# meta description
description: "We're going to have some fun by solving 30 Ruby Coding Challenges in 30 Days for folks who are just getting started and folks who just want to have fun in preparing themselves for coding interviews"

# taxonomies
categories: 
  - "Ruby"
tags:
  - "Ruby Series"
  - "30DaysCoding"

# post type
type: "post"
---

Hey friend!

This is the first Part of this series of **[30 Coding Challenges in Ruby](https://www.youtube.com/watch?v=pfaecP3Wbjw)** for:

- folks who are just getting started
- folks who just want to stretch their brain a little bit
- folks who just want to have fun in preparing themselves for coding interviews

**What about the Ruby environment?**

- No excuses, you don't need that
- [Here is the link for a Ruby Online Compiler](https://repl.it/languages/ruby), which I'm going to share all of the code and you can also play around
- It's all about problem-solving skills and concepts, not about programming languages :)

**The most important goal**: It's all about **having fun** 🕺💃 while solving simple but great **coding challenges**.

## I'm the Problem, Nice to Meet You

> Given an array of numbers, we want to count how many items are greater than 5

Com'on, give us something more difficult and interesting 😒

I know, I know what you're thinking but this is just to start our journey together 😬

I'm going to break this down into **4 steps**:

- Logic to solve the problem
- Solving with classic for loops
- Organizing our code with methods
- Bonus: Meeting Blocks in Ruby

Are you ready? Let's get into it : )

## #1 Logic to Solve the Problem

Yes, the logic is pretty simple. Again, just to stretch our legs and arms to the run

- Given an array
- Go through all of the numbers
- For each number you compare if the number is greater than 5
- You increment a variable (let's call it **count**)
- You print the variable **count** after going through the array

## #2 Classic For Loop Expression

Again, don't worry about the Ruby syntax. Focus on concepts and logic. 

For the code below we've created a classic **for loop expression** and for each **item** in the given array, we're checking if the number is greater than 5, just like the previous logic 

```ruby
array = [15, 7, 3, 2, 17, 12, 1]
count = 0;
for item in array
  if item > 5
    count += 1
  end
end
puts count  # prints out the count value, which is 4. Nice
```

## #3 Organizing with a Method

Nothing special here. Just organizing the kitcken with a method.

Notice that we're taking a **number** as an argument, which will be the number used to compare the items in the array

```ruby
def how_many_are_greater_than(number, array)
  count = 0;
  for item in array
    if item > number
      count += 1
    end
  end
  return count # in Ruby we don't need to use return btw
end

array = [15, 7 , 3, 2, 17, 12, 1]
count = how_many_are_greater_than(5, array) # a little bit better, isn't it?
puts count
```

Pretty simple, right?

What about doing that in a more Rubyish way? 😏

## #4 Hipster Time: Blocks in Ruby

Bonus hipster time.

Ruby (as many other languages) has its own way to do a few things and that is called **Ruby Way** or **Rubyish Way** to do things

An array in Ruby provides a method called **count(),** which receives a **block** that can be an **expression to be evaluated**

```ruby
array.count do |item|
  item > number
end
```

Notice that:

- **item**: is just a single item from our array. This **block** ~~magically~~ automatically executes a **for loop** expression
- **item > number:** is the expression to be **evaluated** for each **item**

The complete code:

```ruby
def how_many_are_greater_than_rubyish(number, array)
  array.count do |item|
    item > number
  end
end

array = [15, 7 , 3, 2, 17, 12, 1]
count = how_many_are_greater_than_rubyish(5, array)
puts count
```

But wait. Where is the **count** variable and **how we return it**? Brillant question.

Ruby **automatically** increments an **internal variable** each time the expression **item > number** is evaluated to **true** and keeps the result in this

internal variable.

When the execution is finished, Ruby automatically **returns the result** for us

Don't believe me? Check the code below:

```ruby
def how_many_are_greater_than_rubyish(number, array)  
  return array.count do |item|
    item > number
  end
end

array = [15, 7 , 3, 2, 17, 12, 1]
count = how_many_are_greater_than_rubyish(5)
puts count
```

Now I'm explicitly using the **return** keyword, which will behave in the same way, returning the final result after the expression being evaluated for each item in the array. 

This is a more declarative approach than an imperative one, but this is a discussion for an upcoming article.

Well done, Ruby! **💪**

That's it. Thanks for your visit, really appreciate your time and see you soon :) 

Let's keep in touch and don't forget to signup for my weekly newsletter

[Twitter](https://twitter.com/_alex_gama/)
[Youtube](https://www.youtube.com/channel/UCn09BXJXOCPLARsqNvxEFuw?view_as=subscriber/)
[Instagram](https://www.instagram.com/_alex_gama)
[Linkedin](https://www.linkedin.com/in/alexandregama/)