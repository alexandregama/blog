---
title: "Day 17 of 30 - Ruby Coding Challenge - Decent Ruby Way to Sum Even Numbers in a Fibonacci Sequence"
date: 2020-06-30T13:49:23+06:00
draft: false

# post thumb
image: "images/post/ruby/ruby-series/day-17-of-30-Ruby-Coding-Challenge-decent-sum-even-numbers-fibonacci-sequence-ruby-way.png"

# meta description
description: "Day 17 of 30 - Ruby Coding Challenges in 30 Days. We're going to sum all the even numbers in a given Fibonacci sequence using a better code design in Ruby"

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

This is the blog post version of the [Youtube video](https://youtu.be/86lEtgO4yTM) from the [30 Ruby Coding Challenges in 30 Days series](https://courses.alexgama.io/course?courseid=ruby-coding-challenges-course)

Today we want to solve the [previous problem](https://youtu.be/hs4cVsva5x4) in a more Ruby Way

> I want to sum all even numbers in a Fibonacci sequence

## Last Algorithm Version

This was the last algorithm version of the problem:

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

The code is not that great for a couple of reasons:

- too many local variables to manipulate
- two main responsibilities: create the Fibonacci sequence **AND** validate even numbers

The 2 main reasons above leave us with a difficult code to read, therefore, a difficult code to maintain. Fewer friends in our team, right? 😅

I'm going to try to get rid of these problems. Let's get into it!

## Better Algorithm Version - Ruby Way

I'm going to break the refactoring into a few small steps

**Step 1 - Splitting Responsibilities**

- let's create a new method do generate only the Fibonacci sequence

```ruby
def fibonacci(count)
  sequence = []
  (0..count).each do |number|
    sequence << number if number <= 1
    sequence << sequence[-1] + sequence[-2] if number > 1
  end
  sequence
end
```

- then we're going to create the method to sum even numbers based on the generated sequence

```ruby
def fibonacci(count)
  sequence = []
  (0..count).each do |number|
    sequence << number if number <= 1
    sequence << sequence[-1] + sequence[-2] if number > 1
  end
  sequence
end

def sum(array)
  # magic here
end

puts sum(fibonacci(10))
```

**Step 2 - Sum of Even Numbers**

Now, we just need to sum all the even numbers, given an array of numbers

As we did [previously here](https://youtu.be/Y3W64fXmfkw), I'm going to use a Ruby symbol, which allows us to reduce a list of items into a single number by applying an operation

```ruby
 def sum(array)
  array.select { |number| number % 2 == 0 }.reduce(:+)
end
```

The complete code would be:

```ruby
def fibonacci(count)
  sequence = []
  (0..count).each do |number|
    sequence << number if number <= 1
    sequence << sequence[-1] + sequence[-2] if number > 1
  end
  sequence
end

def sum(array)
  array.select { |number| number % 2 == 0 }.reduce(:+)
end

puts sum(fibonacci(10))
```

That's it! A little bit better version of the previous problem and I hope you liked it! 

Do you have a better/different version? Drop that in the [Youtube comments](https://youtu.be/86lEtgO4yTM) and bring more healthy discussions 😄

Thanks for the visit and see you in the next coding challenge!

{{< youtube 86lEtgO4yTM >}}

Don't forget to come by and say hi Alex

[Courses](https://courses.alexgama.io/)
[Twitter](https://twitter.com/_alex_gama/)
[Youtube](https://www.youtube.com/c/AlexandreGamaLima)
[Instagram](https://www.instagram.com/_alex_gama)
[Linkedin](https://www.linkedin.com/in/alexandregama/)
[GitHub](https://github.com/alexandregama)