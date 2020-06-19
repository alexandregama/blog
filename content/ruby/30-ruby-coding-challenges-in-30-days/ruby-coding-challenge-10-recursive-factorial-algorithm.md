---
title: "Day 10 of 30 - Ruby Coding Challenge - Recursive Factorial Numbers"
date: 2020-06-19T13:49:23+06:00
draft: false

# post thumb
image: "images/post/ruby/ruby-series/day-9-of-30-Ruby-Coding-Challenge-factorial-ruby-way-2-functional-programming.png"

# meta description
description: "Day 10 of 30 - Ruby Coding Challenges in 30 Days. We're going solve the Factorial problem using recursion in Ruby"

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

Today we're going to solve the previous Factorial problem using **recursion in Ruby 👌**. This is the post version of the [Youtube video](https://www.youtube.com/watch?v=szH91N0HZ_w) :)

Just a reminder, **it doesn't matter** if you're using Ruby, Python, JavaScript, or your favorite language, what really matters is the concepts and logic to solve problems

If you haven't watched the [previous video](https://www.youtube.com/watch?v=szH91N0HZ_w), I just want to remember the definition of a Factorial number

> A Factorial number N is the product of all positive integers less than or equal to the number N

We indicate a Factorial number as **N!**

Real example:

```ruby
5! = 5*4*3*2*1
# result in 120
```

A possible (and not so beautiful) solution to this problem is the solution in the [first video](https://www.youtube.com/watch?v=Ee1p3P-Yx_c):

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

## Recursion

Again, just recalling what the recursion technique is:

> Recursion is when you solve a problem by breaking the problem down into smaller versions of the same problem

And when it comes to coding, the method or function calls on itself :)

Before going to code, let's see the first example:

```ruby
5! = 5*4*3*2*1
```

But you can actually calculate this way:

```ruby
5! = 5*4!
```

Because 4! = 4*3*2*1, which is a small part of the **5!** problem

You can go further and say:

```ruby
5! = 5*4*3!
```

A little bit more

```ruby
5! = 5*4*3*2!
```

And finally

```ruby
5! = 5*4*3*2*1
```

Notice that we've broken that down into smaller Factorial calculations

The recursive Ruby method will be the following:

```ruby
def factorial(number)
  return 1 if number == 0
  return number * factorial(number - 1)
end
```

Notice that:

- returns 1 if the number is equal to 0. That's the criteria to stop the method execution
- returns number * factorial(number - 1) which, as we saw, is a method calling on itself

A more leaner version of this method in Ruby would be:

```ruby
def factorial(number)
  number == 0 ? 1 : number * factorial(number - 1)
end
```

Also notice that:

- We don't need to explicitly use **return** in Ruby
- We're using a ternary condition, which in our case makes the readability (in my opinion) much better

That's it!

Hope you liked it and see you tomorrow in the [next challenge](https://www.youtube.com/watch?v=pfaecP3Wbjw&list=PLEoubTKvE34g5uL5_pg5FOoo3Ae6vlSwu) :)

{{< youtube rB2kEIsGUFc >}}

Don't forget to keep in touch and say hi Alex

[Twitter](https://twitter.com/_alex_gama/)
[Youtube](https://www.youtube.com/channel/UCn09BXJXOCPLARsqNvxEFuw?view_as=subscriber/)
[Instagram](https://www.instagram.com/_alex_gama)
[Linkedin](https://www.linkedin.com/in/alexandregama/)
[GitHub](https://github.com/alexandregama)