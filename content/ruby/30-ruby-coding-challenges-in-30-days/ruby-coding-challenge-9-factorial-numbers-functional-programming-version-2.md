---
title: "Day 9 of 30 - Ruby Coding Challenge - Factorial Numbers - Final Functional Version"
date: 2020-06-11T13:49:23+06:00
draft: false

# post thumb
image: "images/post/ruby/ruby-series/day-9-of-30-Ruby-Coding-Challenge-factorial-ruby-way-2-functional-programming.png"

# meta description
description: "Day 9 of 30 - Ruby Coding Challenges in 30 Days. We're going to finish our journey of writing Factorials in Ruby by changing the previous algorithm a little bit more to reflect a more Ruby way to solve code"

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

In today's post, which is the writing version of the Youtube video, we'll finally finish in an elegant way our journey of writing Factorials in Ruby.

## #1 - Algorithm Version 3. Ruby Rocks

This is the previous solution to our problem if calculating Factorial in Ruby

```ruby
def factorial_version_3(number)
  (1..number).reduce(:*)
end

puts factorial_version_3(5)
```

## #2 - Algorithm Version 4. It Can Be Even Better

Now it's to know the method **downto(),** which can be called in numbers!

We can just ask to Ruby: Can you iterate from a number down to another number?

Take a look at this code:

```ruby
puts 10.downto(1).to_a

# output
10
9
8
7
6
5
4
3
2
1
```

Notice that the result will be numbers between **10 and 1**, which Ruby handles automatically. Nice!

The next (and final) step is just indicate to Ruby the we want a reduced value from this list of numbers.

We can easily do that using the method **reduce()** that we met in the previous algorithm

The final result:

```ruby
def factorial_version_4(number)
  number.downto(1).reduce(:*)
end

puts factorial_version_4(5)
```

Amazing! 

 If you want to compare with the first version:

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

One final note: I completely forgot to validate the Factorial of zero, which is by definition 1. 

I don't want to put complexity, so I'll just add a conditional in the method:

```ruby
def factorial_version_4(number)
  return 1 if number == 0
  number.downto(1).reduce(:*)
end

puts factorial_version_4(0)
```

There we go. Much simpler, which means, more readable and maintainable

Thanks for the visit and see you in the next challenge :)

{{< youtube rB2kEIsGUFc >}}

Don't forget to keep in touch and say hi Alex

[Twitter](https://twitter.com/_alex_gama/)
[Youtube](https://www.youtube.com/channel/UCn09BXJXOCPLARsqNvxEFuw?view_as=subscriber/)
[Instagram](https://www.instagram.com/_alex_gama)
[Linkedin](https://www.linkedin.com/in/alexandregama/)