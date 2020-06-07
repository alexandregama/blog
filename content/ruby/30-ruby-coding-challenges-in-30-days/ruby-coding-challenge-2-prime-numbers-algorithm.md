---
title: "Day 2 of 30 - Ruby Coding Challenge - Ugly Prime Algorithm"
date: 2020-06-07T13:49:23+06:00
draft: false

# post thumb
image: "images/post/ruby/ruby-series/day-1-of-30-Ruby-Coding-Challenge-prime-numbers-arrays.png"

# meta description
description: "Day 2 of 30 - Ruby Coding Challenges in 30 Days. Continuing to stretch our arms and legs to the long run, I'm going to solve a simple and common algorithm: How Many Prime Numbers Are in a Given Array"

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

Day 2 of 30 - Ruby Coding Challenges in 30 Days. This is the post version of the [Youtube video](https://www.youtube.com/watch?v=WT6aoeOsEwY)

Continuing to stretch our arms and legs to the long run, I'm going to solve a simple and common algorithm:

> How Many Prime Numbers Are in a Given Array

How does my brain work when it comes to solving algorithms? Just get the job done!

- Forget about good practices
- Forget about code design
- Especially forget performance

I really love to respect my brain because, well, he can be against me

Today I'll solve this problem with a poor design and you'll feel that sensation that we should not be friends anymore.

But I promise that I'm going to write AT LEAST 4 versions of this Algorithm and maybe you might reconsider our friendship s2

Let's start this conversation refreshing our brain and I hope you don't mind:

## #1 What is a Prime Number

short answer: 

> A natural number greater than 1 that is evenly divided only by 1 and itself

Wikipedia has a really sexy answer.

Going through some examples:

- 1 is prime
- 2 is prime
- 3 is prime
- 4 is not prime. It's divided by 2
- 5 is prime
- 6 is not prime. It's divided by 2 and 3
- 7 is prime
- 8 is not prime. It's divided by 2 and 4
- 9 is not prime. It's divided by 3
- 10 is not prime. It's divided by 2 and 5

Yep, you got it.

## #2 Prime Number Algorithm in Ruby

Are you familiar with Ruby? If yes, then probably you're already aware of the Prime library. This is an unfair advantage. 

I'm going  to talk about that later but for now let's stick with the old and good manual process.

It's time to create the code skeleton. A method waiting for an array:

```ruby
def count_prime_number_version_1(array)
	# magic will happen here
end

array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
puts count_prime_number_version_1(array)
```

Just for clarity, I'm going to create a variable, which indicates the total count:

```ruby
def count_prime_number_version_1(array)
  prime_count = 0
	# a loop expression here
  return prime_count
end

array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
puts count_prime_number_version_1(array)
```

It's time to go through the array and **ask for each item if they are prime or not**

```ruby
def count_prime_number_version_1(array)
  prime_count = 0
  for item in array
		
  end
  return prime_count
end
```

We know that 1 is not prime, so why not just ignore it? 

In Ruby we use **next** to say: "Hey Ruby, forget this item and jump to the next item"

Are you coming from Java, Python or Javascript? That's the same with **continue**

```ruby
def count_prime_number_version_1(array)
  prime_count = 0
  for item in array
		next if item == 1
  end
  return prime_count
end
```

How can we validate in Ruby if a number is divided by another number, resulting in a remainder zero?

With percent %

```ruby
# checking if the remainder value is zero when dividing an item by count
item % count == 0
```

Ok, now we can write a while loop that

- given an item
- check if there's a number that divides the item, remaining in zero

```ruby
is_prime = true

number = item - 1
while number > 1
  if item % number != 0
    number = number - 1
  else
    is_prime = false
    break
  end
end
```

Notice that

- we're using **is_prime** to indicate when an item is, well, prime
- we're using **break** to stop the while loop once the item is divided by a number, which already means that it's not prime

It's time to risk our virtual friendship. The complete code:

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

What I want to prove?

- I write terrible code at first and I'm not even sorry
- I don't worry about design, performance, etc on the first version. Just get the job done (and lose some friends on the way)
- For beginners, it's probably a good way to go through this process

As I said, this algorithm will become beautiful (hopefully), or at least better in the upcoming video and we'll be friends again.

See you

[Twitter](https://twitter.com/_alex_gama/)
[Youtube](https://www.youtube.com/channel/UCn09BXJXOCPLARsqNvxEFuw?view_as=subscriber/)
[Instagram](https://www.instagram.com/_alex_gama)
[Linkedin](https://www.linkedin.com/in/alexandregama/)

{{< youtube WT6aoeOsEwY >}}