---
title: "Day 7 of 30 - Ruby Coding Challenge - Factorial Numbers - Better Version"
date: 2020-06-15T13:49:23+06:00
draft: false

# post thumb
image: "images/post/ruby/ruby-series/day-7-of-30-Ruby-Coding-Challenge-factorial-number-version-2.png"

# meta description
description: "Day 7 of 30 - Ruby Coding Challenges in 30 Days. We're going to explore how to calculate Factorial Numbers in Ruby. This will be a better version that can be still improved later on"

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

In today's post, which is the writing version of the [Youtube video](https://www.youtube.com/watch?v=rdo7G3FPdBw), we'll rewrite the previous algorithm with a little bit better version. It'll be really quick, I promise.

## #1 - Algorithm Version 1. As usual, Ugly

Just to remember, this was the first algorithm version

```ruby
def factorial(number)
  result = number
  while number > 1
    result = result * (number - 1)
    number = number - 1
  end
  return result
end

puts factorial(1)
```

## #2 - Algorithm Version 2. A Little Better

I'd like to keep the argument **number** intact, which means that I don't want to use it to control my while loop

Ruby has an amazing and easy way to deal with arrays in this case

```ruby
(1..(number - 1))
```

With the code above we're saying to Ruby to iterate with numbers between 1 and **number - 1**. 

Notice that **number - 1** is the pattern used for each iteration.

```ruby
(1..(number - 1)).each do |item|

end
```

Notice that the method **each** gives us the current number, which is the **item**, for each iteration

The final version would be:

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

As you can see, we avoid the **number** mutation, which means that our code is less error-prone and easier to read. Cool!

In the next video we'll refactor this code a little bit more to reflect a more Ruby way to solve things. See you there :)

{{< youtube rdo7G3FPdBw >}}

Don't forget to keep in touch and say hi Alex

[Twitter](https://twitter.com/_alex_gama/)
[Youtube](https://www.youtube.com/channel/UCn09BXJXOCPLARsqNvxEFuw?view_as=subscriber/)
[Instagram](https://www.instagram.com/_alex_gama)
[Linkedin](https://www.linkedin.com/in/alexandregama/)
[GitHub](https://github.com/alexandregama)