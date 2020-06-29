---
title: "Day 13 of 30 - Ruby Coding Challenge - Fibonacci Sequence in Ruby"
date: 2020-06-23T13:49:23+06:00
draft: false

# post thumb
image: "images/post/ruby/ruby-series/day-13-of-30-Ruby-Coding-Challenge-fibonacci-sequence.png"

# meta description
description: "Day 13 of 30 - Ruby Coding Challenges in 30 Days. We're going to solve the famous Fibonacci sequence in Ruby. The next videos will be all about getting the algorithm better"

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

This is the blog post version of the [Youtube video](https://youtu.be/rccOdzwtOD0) from the [30 Ruby Coding Challenges in 30 Days series](https://courses.alexgama.io/course?courseid=ruby-coding-challenges-course)

## Fancy Fibonacci Algorithm Definition

- To get the next number in a sequence, you have to sum the previous two numbers.

One important point: The Fibonacci sequence already **starts** with **0** and **1** as the first **2 numbers**

Here is a sequence to help you out a bit more:

```ruby
0 1 1 2 3 5 8 13 21 34 55 88 ...
```

Perfect. Now we want to solve the following puzzle:

> We want to calculate the first N numbers in a Fibonacci sequence

**First Real Example:**

I want to calculate the first 8 numbers in a Fibonacci sequence:

```ruby
0 1 1 2 3 5 8 13
```

**Second Real Example:**

I want to calculate the first 10 numbers in a Fibonacci sequence:

```ruby
0 1 1 2 3 5 8 13 21 34
```

I'm pretty sure you got it : )

## Fibonacci Algorithm in Ruby

**Step 1**

- let's create the **fibonacci()** method
- then we'll start the sequence with 0 and 1

```ruby
def fibonacci(count)
  n1 = 0
  n2 = 1
  sequence = [n1, n2]
end

puts fibonacci(8)
```

**Step 2**

- because the list starts with 2 numbers, we can calculate the next one using a **while loop**

```ruby
def fibonacci(count)
  n1 = 0
  n2 = 1
  sequence = [n1, n2]
  while count > 2 # just a while loop expression that decrements the argument count
    count = count - 1
  end
  return sequence
end

puts fibonacci(8)
# 0 1 1 2 3 5 8 13
```

**Step 3**

- the **next number** is the **sum** of the **previous 2** numbers

```ruby
def fibonacci(count)
  n1 = 0
  n2 = 1
  sequence = [n1, n2]
  while count > 2
		# sum of the previous 2 numbers
    n3 = n1 + n2
    sequence.push(n3)

	  # assigning the new numbers to calculate the next number in the sequence
    n1 = n2
    n2 = n3
    count = count - 1
  end
  return sequence
end

puts fibonacci(8)
# 0 1 1 2 3 5 8 13
```

Pretty simple, isn't it?

Although the code is simple, it's far from a good code design because:

- it lacks readability
- it updates an argument received in the method
- it has too many local variables

To be honest, some times (and even most of the time 😬), a good code design is a matter of context and personal taste and maybe you might think that this code is already good enough and I don't blame you 😅 however I'll solve the same problem using a different approach that probably you might like better

Hope to see you in the next [Ruby Coding Challenge](https://courses.alexgama.io/course?courseid=ruby-coding-challenges-course) : ) 

{{< youtube rccOdzwtOD0 >}}

Don't forget to come by and say hi Alex

[Courses](https://courses.alexgama.io/)
[Twitter](https://twitter.com/_alex_gama/)
[Youtube](https://www.youtube.com/c/AlexandreGamaLima)
[Instagram](https://www.instagram.com/_alex_gama)
[Linkedin](https://www.linkedin.com/in/alexandregama/)
[GitHub](https://github.com/alexandregama)