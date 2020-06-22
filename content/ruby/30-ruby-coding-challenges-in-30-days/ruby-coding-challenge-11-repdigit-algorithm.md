---
title: "Day 11 of 30 - Ruby Coding Challenge - Repdigit Number Algorithm"
date: 2020-06-21T13:49:23+06:00
draft: false

# post thumb
image: "images/post/ruby/ruby-series/day-11-of-30-Ruby-Coding-Challenge-repdigit-number-algorithm.png"

# meta description
description: "Day 11 of 30 - Ruby Coding Challenges in 30 Days. We're going solve the the Repdigit Algorithm, which validates if a digit is repeated in the whole number"

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

This is the blog post version of the [Youtube video](https://www.youtube.com/watch?v=gv3Qddjp5IY) of the [Ruby Coding Challenges in 30 days](https://www.youtube.com/watch?v=pfaecP3Wbjw&list=PLEoubTKvE34g5uL5_pg5FOoo3Ae6vlSwu). 

Today we're going to solve this simple and elegant coding challenge, which is the **Repdigit Algorithm**:

> Given a number, I want to check if the number is composed of repeated instances of the same digit

That was the fancy definition.

Real Life:

```ruby
999999
```

This is a Repdigit (repeated digit) because it **repeats 9 for the whole number**

```ruby
7777
```

This is a Repdigit because it **repeats 7 for the whole number**

```ruby
666664
```

This is not a Repdigit because **it doesn't repeat 6** for the whole number

```ruby
333444777
```

This is not a Repdigit because it doesn't **repeat 3,4 or 7 for the whole number**

I think you got it. Very simple.

## #1 Repdigit Algorithm Solution

One possible solution is

- convert the number into an array
- take the first digit of the number
- check if all of the numbers are the same digit

Pretty simple, right?

Let's see how Ruby handles it. 

**Step 1**

The first step is actually to convert the Integer into a String so that we can be able to manipulate it

```ruby
array = number.to_s
```

**Step 2**

Now it's time to create the array based on that string

```ruby
array = number.to_s.split('')
```

**Step 3**

Finally, let's convert each string in the array back to an integer

```ruby
array = number.to_s.split('').map(&:to_i)
```

**Step 4**

I'm going to take the first digit to compare with all the numbers

```ruby
digit = array.first
```

**Step 5**

Then the final step is to count **how many digits in that number are different from the first digit**

```ruby
array = number.to_s.split('').map(&:to_i)
digit = array.first
count = array.count { |item| item != digit }
```

Perfect! If the **count** variable is different from zero then we have a digit that is different from the first digit, which means that the number is not Repdigit

The final solution would be:

```ruby
def is_repdigit(number)
  array = number.to_s.split('').map(&:to_i)
  digit = array.first
  count = array.count { |item| item != digit }

  if count == 0
    return true
  else
    return false
  end
end

puts is_repdigit(777) # tru
```

## #2 A Leaner Solution in Ruby

A little bit leaner solution would be the following:

```ruby
def is_repdigit_2(number)
  array = number.to_s.split('').map(&:to_i)
  array.count { |item| item != array.first } == 0
end
```

That's it!

In the next video we're going to explore a Ruby Way to solve this algorithm. See you there :)

{{< youtube gv3Qddjp5IY >}}

Don't forget to keep in touch and say hi Alex

[Twitter](https://twitter.com/_alex_gama/)
[Youtube](https://www.youtube.com/channel/UCn09BXJXOCPLARsqNvxEFuw?view_as=subscriber/)
[Instagram](https://www.instagram.com/_alex_gama)
[Linkedin](https://www.linkedin.com/in/alexandregama/)
[GitHub](https://github.com/alexandregama)