---
title: "Day 12 of 30 - Ruby Coding Challenge - Repdigit Number Algorithm in a more Ruby Way"
date: 2020-06-22T13:49:23+06:00
draft: false

# post thumb
image: "images/post/ruby/ruby-series/day-11-of-30-Ruby-Coding-Challenge-repdigit-number-algorithm.png"

# meta description
description: "Day 12 of 30 - Ruby Coding Challenges in 30 Days. We're going solve the the Repdigit Algorithm in a more Ruby way, which validates if a digit is repeated in the whole number"

# taxonomies
categories: 
  - "Ruby"
tags:
  - "Ruby Series"
  - "30DaysCoding"

# post type
type: "post"
---

Hey!

This is the blog post version of the [Youtube video](https://youtu.be/jhUmGRZikKI) from the [30 Ruby Coding Challenges in 30 Days series](https://courses.alexgama.io/course?courseid=ruby-coding-challenges-course)

This post will be really short because Ruby, fortunately, provides us a really good way to solve the [Repdigit Algorithm](https://youtu.be/gv3Qddjp5IY)

## #1 Repdigit Algorithm Version 1

In this solution we're going to take the following steps:

**Step 1**

- given a number, we'll convert it into a String

```ruby
number.to_s
```

**Step 2**

- then we can use the method **squeeze**, which keeps only the unique digits\

```ruby
number.to_s.squeeze
```

**Step 3**

- now we validate if the remainder length of the array is 1

```ruby
number.to_s.squeeze.length == 1
```

The complete code would be:

```ruby
def is_repdigit(number)
	number.to_s.squeeze.length == 1
end

puts is_repdigit(777) # true
puts is_repdigit(774) # false
puts is_repdigit(555555) # true
puts is_repdigit(456555) # false
```

Pretty simple, isn't it? :)

## #2 Repdigit Algorithm Version 2

Another way to solve this problem is manipulating **chars** in Ruby

**Step 1**

- getting the chars from the String

```ruby
number.to_s.chars
```

**Step 2**

- getting the unique chars from the String

```ruby
number.to_s.chars.uniq
```

**Step 3**

- Validating if the length of the array is 1

```ruby
number.to_s.chars.uniq.length == 1
```

The complete code would be:

```ruby
def is_repdigit(number)
  number.to_s.chars.uniq.length == 1
end

puts is_repdigit(777) # true
puts is_repdigit(774) # false
puts is_repdigit(555555) # true
puts is_repdigit(456555) # false
```

Amazing! Ruby allows us to solve the problem in a really beautiful and straightforward way 😃

That's it! I hope you liked it and see you in the [next challenge](https://courses.alexgama.io/course?courseid=ruby-coding-challenges-course) : )

{{< youtube jhUmGRZikKI >}}

Don't forget to come by and say hi Alex

[Twitter](https://twitter.com/_alex_gama/)
[Youtube](https://www.youtube.com/channel/UCn09BXJXOCPLARsqNvxEFuw?view_as=subscriber/)
[Instagram](https://www.instagram.com/_alex_gama)
[Linkedin](https://www.linkedin.com/in/alexandregama/)
[GitHub](https://github.com/alexandregama)