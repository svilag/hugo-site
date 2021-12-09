+++
draft = true
image = "static/img/svilag/ERD_svilag.png"
showonlyimage = true
date = "2021-12-06T20:23:59+05:30"
title = "237 Letters in a Database"
writer = "Shelbie Vilag"
weight = 11
tags = ['SQL', 'Databases', 'History']
categories = ['Project']
+++

As part of a course on SQL and Databases, I created a database in MySQL from the data collected from my Undergraduate Capstone project, "_237 Letters_".
<!--more-->

**The assignment:** select a dataset and create a database in MySQL from that data.

**The Data:** The dataset I used included metadata about 237 letters in the Eastern Michigan University Archives that I used as a part of my undergraduate capstone project in History. These letters were sent to Eastern Michigan Regents in protest of Civil Rights Activist Julian Bond speaking at the January 1971 commencement and receiving an Honorary Doctor of Laws degree.

[View Raw Data](https://raw.githubusercontent.com/svilag/hugo-site/main/content/static/img/svilag/564_project_data_svilag.csv)

**The Process:**

1. First I had to design the database. How was I going to normalize this data so that it could be easily queried?
2. Then, I had to process the data. One CSV had to become six, one for each table that would go into the database.
3. Once I had my tables set as CSV files, I used JetBrains Datagrip to import the data to my database server.
4. After the data was in, I set up my keys to ensure my tables were linked.
5. Ready to query!

## Execution

![Entity Relationship Diagram](https://raw.githubusercontent.com/svilag/hugo-site/main/content/static/img/svilag/ERD_svilag.png)

The data I started with was collected in one single CSV file. This obviously needed to be processed so that the data could be imported to a database that would be easy to query. Using a combination of Google sheets and the Python CSV library, I took the original CSV and filtered through the data I needed to in order to create six tables. [Link to Python Notebook](https://deepnote.com/@svilag/564-final-project-data-Ey9oy3grRCiMjgwOmTwzNQ)



To test it, I chose some questions that I wanted to know the answers to based on the data, and created queries for those questions. The most fun query to put together required a join of all six tables in the database.

#### What letter was sent for the most reasons? What was the quote?

> **Query:** `SELECT cat.category, cl.letter_id, p.name, c.city, l.quote FROM categories cat JOIN cat_link cl on cat.cat_id=cl.cat_id JOIN letters l on l.letter_id=cl.letter_id JOIN cities c on c.city_id=l.city_id JOIN people_link pl on l.letter_id=pl.letter_id JOIN people p on pl.person_id=p.person_id WHERE cl.letter_id = 160 AND p.role LIKE 'sender';`

> **Quote:** "He is a radical and is bound to infect the minds of the student body. Anarchists, Radicals, Socialists, and Communists should not be allowed on our campuses." &mdash;_P. H. MacBride, from Brighton_

>**Query Results:**
>![Query Results](https://raw.githubusercontent.com/svilag/hugo-site/main/content/static/img/svilag/query-results.jpg)

* Lorem ipsum dolor sit amet, consectetuer adipiscing elit.
* Aliquam tincidunt mauris eu risus.

When she reached the first hills of the Italic Mountains, she had a last view back on the skyline of her hometown Bookmarksgrove, the headline of Alphabet Village and the subline of her own road, the Line Lane. Pityful a rethoric question ran over her cheek, then  

The database was executed successfully! :tada:

