---
title: "Day 18 of 30 - Ruby Coding Challenge - Finding the Missing Number Game"
date: 2020-07-06T13:49:23+06:00
draft: false

# post thumb
image: "images/post/ruby/ruby-series/day-18-of-30-Ruby-Coding-Challenge-game-missing-number.png"

# meta description
description: "Day 18 of 30. We're going to play a game: find the missing number in a given array. This first solution will be not that great but we'll get the job done!"

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

This is the blog post version of the [Youtube video](https://youtu.be/9-lbnrgD7-8) from the [30 Ruby Coding Challenges in 30 Days series](https://courses.alexgama.io/course?courseid=ruby-coding-challenges-course)

Let's go straight to the point

## **Coding Challenge**

> Create a function that takes an array of numbers between 1 and 10 (excluding one number) and returns the missing number.

A few points:

- The array of numbers will be unsorted (not in order).
- Only one number will be missing.

Examples

```ruby
find_missing_num([1, 2, 3, 4, 6, 7, 8, 9, 10]) ➞ 5

find_missing_num([7, 2, 3, 6, 5, 9, 1, 4, 8]) ➞ 10

find_missing_num([10, 5, 1, 2, 4, 6, 8, 3, 9]) ➞ 7
```

Pretty simple, isn't it?

## Algorithm in Ruby

Let's break the algorithm down to a few small steps:

**Step 1**

- We need to go through a list of items (an array), going from 1 to 10

```ruby
def find_missing_num(array)
  [1, 2, 3, 4, 5, 6, 7, 8, 9, 10].each do |item|
	end
end

array = [1, 2, 3, 4, 6, 7, 8, 9, 10]
find_missing_num(array)
```

Ruby provides us a really better way to do this:

```ruby
def find_missing_num(array)
  (1..10).each do |item|
	end
end

array = [1, 2, 3, 4, 6, 7, 8, 9, 10]
find_missing_num(array)
```

**Step 2**

- We're going to **compare** each number (from 1 to 10) with the numbers in the **given array**

```ruby
def find_missing_num(array)
  (1..10).each do |item|
    array.each do |number|
      if item == number
        break # breaking the execution
      end      
    end
  end
end

array = [1, 2, 3, 4, 6, 7, 8, 9, 10]
find_missing_num(array)
```

We break the execution once if find the desired number because we don't need to continue looking for the number

**Step 3**

- Because we want to return the number that wasn't found in the array, I'm going to create a local variable to indicate that

```ruby
def find_missing_num(array)
  (1..10).each do |item|
    found = false
    array.each do |number|
      if item == number
        found = true
        break
      end      
    end
    if found = false
      return item
    end
  end
end

array = [1, 2, 3, 4, 6, 7, 8, 9, 10]
find_missing_num(array)
```

That's it!

I know, that's not beautiful but it works : )

Do you have a better/different version? Drop that in the [Youtube comments](https://youtu.be/9-lbnrgD7-8) and bring more healthy discussions 😄

Thanks for the visit and in the [next coding challenge](https://courses.alexgama.io/course?courseid=ruby-coding-challenges-course) we're going to explore a more decent way to solve this puzzle, see you there!

{{< youtube 9-lbnrgD7-8 >}}

Don't forget to come by and say hi Alex

[Courses](https://courses.alexgama.io/course?courseid=ruby-coding-challenges-course)
[Twitter](https://twitter.com/_alex_gama/)
[Youtube](https://www.youtube.com/c/AlexandreGamaLima)
[Instagram](https://www.instagram.com/_alex_gama)
[Linkedin](https://www.linkedin.com/in/alexandregama/)
[GitHub](https://github.com/alexandregama)