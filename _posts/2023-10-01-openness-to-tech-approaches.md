---
layout: post
title: What if there's more than one way to do something correctly?
subtitle: How considering different perspectives can lead to growth and development
cover-img: /assets/img/chicago_lakefront.jpg
thumbnail-img: /assets/img/chicago_lakefront.jpg
share-img: /assets/img/chicago_lakefront.jpg
tags: [tech, software_tooling, personal_growth]
---

After getting several years of technical experience under my belt and working with software veterans with strong convictions, I started to develop my own beliefs about good and bad software engineering practices. There's nothing wrong with that, in fact, it's important because that leads to a deeper understanding of the material, and ultimately your own personal style. The problem as I see it now, is that I held onto these beliefs so stringently that they didn't allow any room for me to understand why someone would take an approach that I saw as unfavorable, and in some cases, convince me that a technical approach that I completely wrote off might not be so bad after all.

Over the last year and a half or so I have noticed a major shift in the way I consider different technical approaches without applying a quick judgement of right or wrong. I think this came from seeing *good* applications of techniques that I previously thought were all bad. 

A good example of this is is when I first starting working on a new team doing business intelligence work writing a lot of SQL. I didn't have any prior experience working with SQL so I sought a lot of guidance from very experienced team members. My team was very against using CTEs (common table expressions) and they believed queries were cleaner and more readable as nested or correlated subqueries. When I went to work Craftsy, the data was very flattened out in a large star schema (compared to the data I worked with on the previous team which was in a snowflake schema) and writing everything in subqueries was much more difficult. Nonetheless, I was determined to write all my SQL in subqueries because that was what I learned was best practice and I could not be convinced otherwise. 

Several years later, I started by job at eSpark Learning and here I was still trying to write all SQL in subqueries. I remember checking in this monster query with a nested subquery in it, and it got ripped apart in code review by my peers. I talked through the review with our Senior Data Scientist to better understand why it would make more sense to rewrite the query with CTEs. I wasn't obstinate about changing the query, but I needed to be convinced that this technical approach that I thought was a bad practice, actually made way more sense than the one that I thought was so great. First we looked at the query plan and I saw how the monster query I had written was slower than writing the same thing with CTEs. Then we talked about debugging and readability. One of the frustrating aspects of SQL is how difficult it can be to debug large, complicated queries when they aren't working properly. CTEs help break up some of that logic so things can be tested in chunks to find the problem more quickly. This is all it took for me to drop my stronly held belief that all CTEs are bad, and I now see the situations in which they make a lot of sense.

I had a similar feeling working with Ruby on Rails for the first time; the syntax was unnecessarily complicated, the shorthand abbreviations were unintuitive, and the way it interacts with the database was messy. Over the last two years I've had the opportunity to learn from skilled Ruby on Rails engineers on my team, and I've built really cool projects from Rails classes I've done on Udemy, which has made me grow to appreciate Ruby on Rails and it's applications.

It must be a part of my own personal development as I grow as an engineer, but I am certainly making an effort and noticing a huge change in my openness and willingness to understand and accept different technical perspectives. There's so much to learn in taking the time to understand different ideas.

Photo: Lake Michigan in Chicago, IL