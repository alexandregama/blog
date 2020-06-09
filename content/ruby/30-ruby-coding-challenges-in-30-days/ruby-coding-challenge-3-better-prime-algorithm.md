---
title: "Day 3 of 30 - Ruby Coding Challenge - Better Prime Algorithm :)"
date: 2020-06-07T13:49:23+06:00
draft: false

# post thumb
image: "images/post/ruby/ruby-series/day-2-of-30-Ruby-Coding-Challenge-prime-numbers-algorithm.png"

# meta description
description: "Day 3 of 30 - Ruby Coding Challenges in 30 Days. It's time to use some Ruby power to solve the previous coding challenge, which was writing an algorithm to count how many prime items exist in an array"

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

Day 3 of 30: Ruby Coding Challenge number 3.

This is the post version of[] this video on Youtube]()

[In the previous video](https://www.youtube.com/watch?v=WT6aoeOsEwY) we solved a really common challenge:

> How many prime items are in a given array

The final code was terrible. However, I'm not even sorry. Remembering why:

- How does my brain work when it comes to solving algorithms? Just get the job done! Decorate after that.

When it comes to algorithms, decoration means a few things:

- Better performance
- Better readability
- Better maintainability

Well, better code design

Today I'll solve the same problem with (I hope) a better code design:

Below you can see the first ugly version:

## #1 - Ugly Algorithm Version

```ruby
def count_prime_number_version_1(array)
  prime_count = 0
  for item in array
    next if item == 1
    is_prime = true

    number = item - 1
    while number > 1
      if item % number == 0
        is_prime = false
        break
      else
        number = number - 1
      end
    end

    if is_prime
      prime_count = prime_count + 1
    end
  end
  return prime_count
end

array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
puts count_prime_number_version_1(array)
```

It's time to organize the kitchen. It would be great to have a method that verifies if a given number is prime.

## #2 - Method Organization

We have 2 main responsibilities

- iterate over the array, asking questions
- validate if a given number is prime or not

I'm going to split this into 2 methods, which will have those responsibilities above:

```ruby
def count_prime_number_version_2(array)
  count_prime = 0
  for item in array
    if is_prime(item) # the new method. it's better. It's clearer
      count_prime = count_prime + 1
    end
  end
  return count_prime
end

def is_prime(item)
  return false if item == 1

  count = item - 1
  while count > 1
    if item % count == 0
      return false
    end
    count = count - 1
  end
  return true
end
```

Cool. It's time to bring some Ruby power and use Ruby Blocks with the count method, which we [did in in the first video](https://www.youtube.com/watch?v=1o95D7as27Q)

```ruby
def count_prime_number_version_2(array)
  array.count do |item|
    is_prime_number(item)
  end
end
```

## #3 - Ruby Arrays

II don't know about you, but I hate local variables. 

It's time to get rid of them. In Ruby it's possible to indicate which items should be created in an array, given

- the initial number
- the pattern to generate the next number

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

Amazing, isn't it?

## #4 - Cheating: Ruby Prime Library

Now that we know how to create the Algorithm manually, it usually doesn't make sense in real life

Ruby has a **Prime** Library, which can get the job done easily.

We just ask if the number is prime or not. Notice that we're importing the Prime library

```ruby
require 'Prime'

Prime.prime?(item)
```

Going ahead and replacing the **is_prime(item)** method:

```ruby
def count_prime_version_6(array)
	array.count do |item|
    Prime.prime?(item)
  end
end
```

And that's our final version, a little bit different than the first one 😏

```ruby
def count_prime_final_version(array)
	array.count do |item|
    Prime.prime?(item)
  end
end

array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
puts count_prime_final_version(array)
```

That's it. I hope that you've learned 1 thing or 2 : )

{{< youtube Y3W64fXmfkw >}}

Thinking out loud here, probably the next coding challenge will be rewriting the Algorithm manually using Recursion 😏

Thanks for your visit, let's keep in touch and see you!

[Twitter](https://twitter.com/_alex_gama/)
[Youtube](https://www.youtube.com/channel/UCn09BXJXOCPLARsqNvxEFuw?view_as=subscriber/)
[Instagram](https://www.instagram.com/_alex_gama)
[Linkedin](https://www.linkedin.com/in/alexandregama/)