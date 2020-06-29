---
title: "Day 14 of 30 - Ruby Coding Challenge - Fibonacci Sequence in Ruby Way"
date: 2020-06-25T13:49:23+06:00
draft: false

# post thumb
image: "images/post/ruby/ruby-series/day-14-of-30-Ruby-Coding-Challenge-fibonacci-sequence-ruby-way.png"

# meta description
description: "Day 14 of 30 - Ruby Coding Challenges in 30 Days. We're going to solve the famous Fibonacci sequence in a more Ruby Way, which will be much better than the previous solution"

# taxonomies
categories: 
  - "Ruby"
tags:
  - "Ruby Series"
  - "30DaysCoding"

# post type
type: "post"
---

HHey friends!

This is the blog post version of the [Youtube video](https://youtu.be/2zMUGAD6s6A) from the [30 Ruby Coding Challenges in 30 Days series](https://courses.alexgama.io/course?courseid=ruby-coding-challenges-course)

## Fibonacci Sequence

It's time to organize the kitchen and to get a better code design to solve the Fibonacci Sequence, which was the [previous coding challenge](https://youtu.be/rccOdzwtOD0):

> We want to calculate the first N numbers in a Fibonacci sequence

This was the last coding solution:

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

You can be honest, not that great 😅

## Ruby Way to Solve the Fibonacci Problem

**Step 1**

Ruby allows us to go from one number to another in a sequence like this:

```ruby
(0..10).each do |number|
end
```

In our example we want:

- to avoid the count mutation (fancy name for change)

We can do that by the following code:

```ruby
(0..count).each do |number|
end
```

That's great because Ruby will **automatically iterate over the array**

**Step 2**

A better way to store the number in the sequence would be:

```ruby
sequence << number if number <= 1
sequence << sequence[-1] + sequence[-2] if sequence.length >= 2
```

The complete code, a little bit leaner with a better strategy, would be 😬:

```ruby
def fibonacci(count)
  sequence = []  
  (0..count).each do |number|
    sequence << number if number <= 1
    sequence << sequence[-1] + sequence[-2] if sequence.length >= 2
  end
  sequence
end
```

Fantastic! Ruby deals with the problem really well! 👌

The next coding challenge is solving the same problem recursively, which is usually harder to think about 🧐 however it has an even better syntax . See you there!

{{< youtube 2zMUGAD6s6A >}}

Don't forget to come by and say hi Alex

[Courses](https://courses.alexgama.io/)
[Twitter](https://twitter.com/_alex_gama/)
[Youtube](https://www.youtube.com/c/AlexandreGamaLima)
[Instagram](https://www.instagram.com/_alex_gama)
[Linkedin](https://www.linkedin.com/in/alexandregama/)
[GitHub](https://github.com/alexandregama)