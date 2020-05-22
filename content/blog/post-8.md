---
title: "Postgres for Beginners Part 1 - I'm PostgreSQL, nice to meet you!"
date: 2019-05-21T20:00:47+06:00
draft: true

# post thumb
image: "images/post/postgres-test-5.jpg"

# meta description
description: "this is meta description"

# taxonomies
categories: 
  - "Database"
tags:
  - "PostgreSQL"
  - "Relational Database"
  - "Beginners Tutorial"

# post type
type: "post"
---

Hey friend!

This will be (hopefully) an amazing journey. Be ready! 6 days of PostgreSQL Database for folks who are just getting started.

I'm a spoiler person, I can't hold secrets with me. Let's explore PostgreSQL from the ground up through the parts below.

- Part 1 - Let's meet PostgreSQL. Theory is here. What it is. Who is using it. Where we can use it
- Part 2 - It's time to play around. It's time to get our environment ready 🚀
- Part 3 - Creating Tables, Storing Data and Altering Structure are beautiful and easy things to do.
- Part 4 - How to Filter Data using the famous SELECT statement
- Part 5 - It's time to Join Tables. Data usually like each other and has a great relationship
- Part 6 - Let's face real life: Operations and Functions in your Postgres tool belt

## 1 - I'm PostgreSQL, nice to meet you :)

PostgreSQL is really easygoing. For now on, I'll call it just Postgres. 

What is Postgres in a picture:

![image](../../images/post/postgres-test-8.jpg)

Going a little bit further

**Postgres is a** **Relational Database**

- Postgres is a powerful **object-relational database** with more than **30 years** of development
- it's called relational database because it follows a certain structure, which has a collection of Tables and each table has Columns and Rows that we use to store data. More on that in a bit

**Postgres is Open Source**

- It is a free and open source project and has a strong and loving community. Did I say it's **free**?
- You can easily extend and modify the codebase. You can even create **other databases** on top of Postgres. Crazy?

**Postgres is Cross Platform**

- Postgres is cross platform, which means that you can use many different programming languages. Amazing!
- You can also install it in many different platform flavors. Mac, Windows, Linux, BSD and Solaris are more than welcome :)

**Postgres has a remarkable Performance and Scalability!**

- By default, Postgres tries to guess the best performance on average hardware and application
- You can easily scale up your Postgres database when needed.
- When it comes to searching data, Postgres provides us a set of Algorithms that can boost searching operations
- If you want to get to the next level, you can even run your things in parallel
- Many Cloud companies allow you to easily add more servers to your Postgres application
- More on this in my upcoming Postgres Performance course

**Postgres is really...really...Reliable!**

- You can trust in Postgres. It won't let you down. Postgres never crashes. Ok, almost never crashes
- If you suffer a power loss, Postgres will keep the data that you previously executed in a safe place for you s2
- More on this in my upcoming Postgres Performance course

**Postgres is EASY to use**

- I'm not a smart guy, however, even I can use it!

Postgres statistics stolen from Postgres Documentation

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/51cc80cb-6e83-4124-9f9a-f5d40e047555/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/51cc80cb-6e83-4124-9f9a-f5d40e047555/Untitled.png)

## 2 - Where is PostgreSQL used?

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0e803e0e-c846-40ea-9695-7615bace29b4/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0e803e0e-c846-40ea-9695-7615bace29b4/Untitled.png)

**Web and Mobile development**

- Postgres provides us great drivers for many programming languages, which allows us to connect with the database using Java, Ruby, Python, Haskell "your favorite language here"
- Probably this is the default mode of Postgres usage

**Extensions**

Postgres provides a great set of APIs that we can extend and create plugins or even a new database

- PostGIS, which is an extension to Postgres that allows us to work with Spatial and Geographic Data
- PipelineDB for time-series aggregation, which is a way to analyze data over time. It's a database on top of Postgres. Amazing!
- TimeScaleDB for scalable SQL queries for time-series data. It's also a database on top of Postgres!

**Data Science**

- Postgres supports a huge amount of data and supports JSON-B for documents and PostGIS for Geolocation, which are topics we will explore later
- Data Analysis through simple and complex queries
- Data Warehousing, which is a place where we store data from multiple sources for data analysis
- Data Mining, which is a technique that allows us to have useful information from data

**NoSQL**

- Postgres NoSQL is the powerful combination of unstructured and relational database technologies in a single database

## 3 - Who is using PostgreSQL?

- A few small and unknown companies around the globe :smirk

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/71f5d0c2-3f31-4ce1-b8cb-5d29a6976342/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/71f5d0c2-3f31-4ce1-b8cb-5d29a6976342/Untitled.png)

## 4 - Database Structure

Let's revisit what is a relational database:

**in a nutshell**

- a structured way to store and retrieve your data

**Some background History (I love History!)**

*Edgar F. Codd* described in 1969 a really special relational model where:

- data is **represented** following a certain structure, which was called **Tuples**, a fancy name. Good name for us: **Rows**
- data is **grouped** following a certain structure, which was called R**elations,** another fancy name. Good name for us: **Tables**
- data is **identified** by following a certain structure, which was called **Fields**, ok not that fancy. Good name for us: **Columns**

Databases that follow the structures above are called **Relational Databases**

Why do we need this relational model? Well:

- it provides a good way to store data and retrieve that data later

**Thinking about a real example, isn't it?**

Let's say that we're building an application to allow **students** to enroll to **courses**

To store students, we will create a **Table** called **Students**

To store courses, we will create a **Table** called **Courses**

- drawing here

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3ca66a79-96a7-49bb-a0b5-dd91876a9c55/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3ca66a79-96a7-49bb-a0b5-dd91876a9c55/Untitled.png)

How can we relate Students to specific Courses? I'll let you with some suspense today. Wait for upcoming posts.

## 5 - How do I manipulate data? SQL Language comes to scene

We manipulate data through a Language that Structures Queries, which are questions or afirmations we want to make

In a different order, we have a **S**tructured **Q**uery **L**anguage, which is a **declarative** way to ask for data

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c05bfda2-2b35-4495-89d7-d98af7de1d94/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c05bfda2-2b35-4495-89d7-d98af7de1d94/Untitled.png)

## 6 - Is there more Languages? Yes! SQL Sub Languages

SQL is broken down into some Sub Languages that allows us to be a little bit more specific on what we want. I'll show you the 4 most important (IHMO)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/710c38e2-a538-44b6-bda8-55bec31955f7/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/710c38e2-a538-44b6-bda8-55bec31955f7/Untitled.png)

Boring text just to Google find it better ¬¬

**DDL - Data Definition Language**

- Related to database structure
- Used to create, alter or delete objects like Tables, Indexes, and Sequences

**DML -** **Data Manipulation Language**

- Related to data manipulation
- Used to select, insert, update and delete data
- Disclaimer: I'm using **Select** here but many people like to use its own sub language - DQL - Data Query Language

**DTL - Data Transaction Language**

- Related to data saved into database...forever :)
- Used to insert, update and remove data permanently. We'll dive into details in an upcoming post, don't worry

**DCL - Data Control Language**

- Related to user privileges on accessing data
- Used to give or remove user access

That's it for today

I know, lots of concepts and information and zero coding. Don't be mad at me. 

One of the most important things in being a **developer/software engineer/geek/you name it** is the ability to truly

understand theory and concepts.

I might confess: I usually like to start coding before going through concepts and I explain concepts **while I'm coding** but for some reason I don't like to do it when it comes to Databases. Probably some internal mental block

Would be great to have your feedback so I can improve things on the upcoming articles

Hope you have learned 1 thing or 2.

Thanks for the visit, I really appreciate :)