---
title: "Day 5 of 30 - Ruby Coding Challenge - Sum Prime Numbers Functionally"
date: 2020-06-11T13:49:23+06:00
draft: false

# post thumb
image: "images/post/ruby/ruby-series/day-5-of-30-Ruby-Coding-Challenge-prime-algorithm-functional-programming.png"

# meta description
description: "Day 5 of 30 - Ruby Coding Challenges in 30 Days. We're going to solve the problem of getting the sum of prime numbers a given array using functional programming with Ruby"

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

Day 5 of 30 of this [Ruby Coding Challenge series](https://www.youtube.com/watch?v=pfaecP3Wbjw) and this is the post version [of the Youtube video](https://www.youtube.com/watch?v=rB2kEIsGUFc).

Today we'll explore the following problem:

> Generate a Sum of Prime Numbers in a Given an Array

The [previous Ruby Coding Challenge](https://www.youtube.com/watch?v=cO9dNVzjz8c) was about counting how many items are prime in a given array. 

This one is quite similar and as usual, we'll:

- solve the problem manually
- solve the problem in a more lovable Ruby way

Let's get into it

## #1 - Let's Revisit the Previous Ruby Coding Challenge

Below we have the final version of our algorithm in Ruby, which has the method **count_prime_numbers()**

```ruby
def count_prime_numbers(array)
  array.count do |item|
    is_prime(item)
  end
end

def is_prime(item)
  return false if item == 1

  (2..(item - 1)).each do |number|
    if item % number == 0
      return false
    end
  end
  return true
end

array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
puts count_prime_numbers(array)
```

## #2 - Creating the Sum Method

Let's replace the **count_prime_numbers()** method by a method that sum the prime numbers, which will be creatively called **sum_prime_numbers():**

The new method should:

- iterate over the array
- check if the current item is prime
- sum the prime item

Pretty simple. Translating into Ruby code:

```ruby
def sum_prime_number(array)
  sum = 0
  for item in array
    if is_prime_number(item)
      sum += item
    end
  end
  return sum
end

array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
puts sum_prime_number(array)
```

Cool. But what about the lovable Ruby way to solve problems? 

## #3 - Ruby Way

One important Ruby style is that we can manipulate arrays without worrying about temporary variables. Nice!

Going in parts, we can at least two favors to Ruby:

- Hey Ruby, given an array, select only items that match a specific condition

```ruby
array.select { |item| is_prime(item) }
```

Beautiful. Almost plain English.

If you execute the code above, you'll end up with a smaller array, with only prime numbers:

```ruby
array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
puts array.select { |item| is_prime(item) }
# result: [2, 3, 5, 7]
```

The next step is asking Ruby another favor:

- Hey Ruby, by the way, now that you have an array with only prime numbers, reduce this array into a sum of all of the items

```ruby
array.select{ |item| is_prime(item) }.reduce(:+)
```

Beautifully, Ruby has the method **reduce()**, which receives the **+ method** that will be used to sum all of the items

The complete code:

```ruby
def sum_prime_number(array)
	array.select{ |item| is_prime(item) }.reduce(:+)
end

def is_prime(item)
  return false if item == 1

  (2..(item - 1)).each do |number|
    if item % number == 0
      return false
    end
  end
  return true
end

array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
puts sum_prime_number(array)
```

Notice that we ended up by having a more functional style, since this code is more declarative. I'm preparing a series to explore Functional Programming in JavaScript, Python, Java, and Ruby with some comparisons with Haskell. I hope to get you into this journey :)

I Hope that you've enjoyed 1 thing or maybe 2 and see you in the next coding challenge :)

{{< youtube rB2kEIsGUFc >}}

Don't forget to keep in touch and say hi Alex

[Twitter](https://twitter.com/_alex_gama/)
[Youtube](https://www.youtube.com/channel/UCn09BXJXOCPLARsqNvxEFuw?view_as=subscriber/)
[Instagram](https://www.instagram.com/_alex_gama)
[Linkedin](https://www.linkedin.com/in/alexandregama/)