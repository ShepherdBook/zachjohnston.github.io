---
layout: post
title: "Debugging is harder when you make assumptions"
author: Zach
---

We received a support ticket complaining that a certain web app was not loading.  When we checked, it was loading intermittently but very slowly, indicating a timeout of a slow-running SQL query.  Once we identifed the query (located within a stored procedure), we unplugged the slow query by returning an empty set.  This allowed the web app to run, albeit without the data from this query.  This gave us time to examine it in detail.

It certainly wasn't the simplest query, considering it was supposed to return a count of thank-you notes sent and received by each of the company's departments.  To make it even more of a challenge, the app's documentation mentioned this query's data set only briefly, and its author had long since left the company.

As we began debugging, we tried to decide between taking the original query apart, and writing a new query from scratch.  Since we had so little information, the solution ended up being a bit of both.

I began re-writing it from scratch using CTEs (instead of the original's nested subqueries).  As I re-wrote it, I became convinced that the original author had missed the mark and was returning incorrect numbers.  My query was correct, I was sure of it.  But these numbers were tracked as department-level metrics, so I couldn't propose changing them without specific justification.

Several frustrating hours later, I realized that an assumption made within the first 30 minutes of debugging was incorrect, and the author's intent became clear.  Now that I understood what the original query was supposed to do, my CTE solution was easily re-written to return the same numbers in a performant manner.

It's tempting to move quickly when trying to understand someone else's existing work, but in this case, I was so excited to create my own solution that I missed a key requirement of the system.  Until I realized my mistake, I was assuming that someone else had written buggy code.  While their code may have been difficult to understand, they knew exactly why they were writing it.  Had I taken the time to understand their code, and realize that I was making assumptions, my new and improve query would have been ready to ship in half the time.  Also, and more importantly, I would not have spent several frustrated hours thinking my predescessor was writing sloppy code. 
