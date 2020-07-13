---
title: "Day 19 of 30 - Ruby Coding Challenge - Finding the Missing Number - Ruby Way"
date: 2020-07-07T13:49:23+06:00
draft: false

# post thumb
image: "images/post/ruby/ruby-series/day-19-of-30-Ruby-Coding-Challenge-game-missing-number-ruby-way.png"

# meta description
description: "Day 19 of 30. We're going to play a game: find the missing number in a given array. This second solution will be a little bit better than the previous one and you'll see why"

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

Today we want to solve the previous puzzle using a more Ruby/Decent way to solve problems. Let's get into it!

## Previous Algorithm Version

The previous algorithm version looks like this:

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

## New Algorithm Version

It's time to avoid manipulating the array manually. We can easily do that by using the method **include?()** on the array

```ruby
arr.include?(number)
```

The simple and complete code could be:

```ruby
def missing_num(arr)
  (1..10).each do |num|
    return num unless arr.include?(num)
  end
end

array = [1, 2, 3, 4, 5, 7, 8, 9, 10]
missing_num(array)
```

Pretty simple, isn't it? 😎

Do you have a better/different way to solve this? Drop your comment on the Youtube video and bring more ideas to the community 😄

See you in the [next coding challenge](https://courses.alexgama.io/course?courseid=ruby-coding-challenges-course) :)

{{< youtube 3jI56aWn4IY >}}

Don't forget to come by and say hi Alex

[Courses](https://courses.alexgama.io/course?courseid=ruby-coding-challenges-course)
[Twitter](https://twitter.com/_alex_gama/)
[Youtube](https://www.youtube.com/c/AlexandreGamaLima)
[Instagram](https://www.instagram.com/_alex_gama)
[Linkedin](https://www.linkedin.com/in/alexandregama/)
[GitHub](https://github.com/alexandregama)