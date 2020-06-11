---
title: "Day 4 of 30 - Ruby Coding Challenge - Prime Algorithm Recursively"
date: 2020-06-07T13:49:23+06:00
draft: false

# post thumb
image: "images/post/ruby/ruby-series/day-4-of-30-Ruby-Coding-Challenge-prime-algorithm-recursively.png"

# meta description
description: "Day 4 of 30 - Ruby Coding Challenges in 30 Days. I want to rewrite the previous coding challenge using recursion, which was counting how many items are in a given array"

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

Day 4 of 30: Ruby Coding Challenge number 4. This is the post version of the [Youtube video](https://www.youtube.com/watch?v=cO9dNVzjz8c)

I want to rewrite the [coding challenge number 3](https://www.youtube.com/watch?v=Y3W64fXmfkw) using **recursion**, which was:

> How many prime items are in a given array?

Let's get into it.

## #1 - First Algorithm Version

It was the final algorithm version:

```ruby
def count_prime_number_version_2(array)
  array.count do |item|
    is_prime_number(item)
  end
end

def is_prime_number(item)
  return false if item == 1

  (2..(item - 1)).each do |number|
    if item % number == 0
      return false
    end
  end
  return true
end

array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
puts count_prime_number_recursively(array)
```

Instead of having that array loop in the **is_prime_number()** method:

```ruby
def is_prime_number(item)
  return false if item == 1

  (2..(item - 1)).each do |number|
    if item % number == 0
      return false
    end
  end
  return true
end
```

We're going to rewrite this method using **recursion**.

## #1 Recursive Algorithms

I know. Recursion is one of the monsters when it comes to coding, along with memory management and giving names to variables.

Just a quick reminder:

> A recursive algorithm calls itself with a smaller version of its own problem

I'm not going to go into much detail about recursion because I'm kind of assuming you already know something about it, however, I might be wrong. Because of that, I'm recording and writing a special tutorial to go through the benefits (and some costs) of recursive algorithms 😏

**Step 1:**

- A recursive function calls itself

```ruby

def is_prime_number(item)
  return is_prime_number(item)
end
```

**Step 2:**

- we need at least one condition to call the function again, which is when **item is not evenly dividable by number**

```ruby

def is_prime_number(item)
  return is_prime_number(item) if item % number != 0
end
```

**Step 3:**

- we already know that 1 is not a prime number as we've seen in the [previous algorithm](https://www.youtube.com/watch?v=Y3W64fXmfkw)

```ruby
def is_prime_number(item)
	return false if item == 1

  return is_prime_number(item) if item % number != 0
end
```

**Step 4:**

- we should call the method itself with the current **number - 1**, which is the logic we have using so far

```ruby
def is_prime_number(item, number)
	return false if item == 1

  return is_prime_number(item, number - 1) if item % number != 0
end
```

**Step 5:**

- we should **return true if numbers reaches 1**, which means that the number is actual prime

```ruby
def is_prime_number(item, number)
	return false if item == 1
	return true if number == 1
  return is_prime_number(item, number - 1) if item % number != 0
end
```

The entire code is:

```ruby
def count_prime_numbers(array)
  array.count do |item|
    is_prime_number(item, item - 1)
  end
end

def is_prime_number(item, number)
	return false if item == 1
	return true if number == 1
  return is_prime_number(item, number - 1) if item % number != 0
end

array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
puts count_prime_numbers(array)
```

And that's it!

To be honest, this is not an easy topic (at least for me) to explain in writing and maybe you [get a better picture watching the video :)](https://www.youtube.com/watch?v=cO9dNVzjz8c)

Just a reminder. This is not about Ruby, it's all about concepts and logics and having some fun while solving these problems.

{{< youtube cO9dNVzjz8c >}}

Thanks for your visit, let's keep in touch and see you in the next challenge :)

[Twitter](https://twitter.com/_alex_gama/)
[Youtube](https://www.youtube.com/channel/UCn09BXJXOCPLARsqNvxEFuw?view_as=subscriber/)
[Instagram](https://www.instagram.com/_alex_gama)
[Linkedin](https://www.linkedin.com/in/alexandregama/)