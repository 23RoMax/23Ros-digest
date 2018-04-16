---
title: "How-To: Increment Selected Values Inside Insert Statement"
date: 2018-04-12T01:16:57+02:00
draft: false
categories: ["postgresql", "rdbms", "SQL"]
tags: ["SQL", "programming", "SQL snippets", "sql magic"]
description: "How-To: Increment Selected Values Inside Insert Statement"
keywords: ["SQL", "programming", "SQL snippets", "23Ro", "sql", "magic"]
---

Welcome to my first snippet addition to this website. I hope you find this as helpful as I find it sometimes.

# Why would I need this?
Imagine you want to fill a field of a table with a sequenctially value, but do not have any ID for a sequence and are using PostgreSQL, and you also already have information in this table that you want to append on. Well there is this option to use the internal ID (CID) provided by PostgreSQL, but this only works to a certain extent. And it won't work if you have more than one combination to fulfill. 
E.g. you want to increment Field 1 but let Field 2 stay the same until a threshold or other condition is fulfilled? This is a very simple solution for the mentioned problem:


myTable:
```
| id            | myIncrement   | other |
| ------------- |:-------------:| -----:|
| UUIDX         | 1             | 1600  |
| UUIDY         | 2             | 1600  |
| UUIDZ         | 3             | 1600  |
```
id type uuid
myIncrement type varchar
other type varchar 

If you already have INT fields, the better.

## Solution proposal
```sql
INSERT INTO myTable(myIncrement, other, id) VALUES (
    (SELECT (myIncrement::INT + 1) FROM myTable ORDER BY myTable DESC LIMIT 1),
    (SELECT other FROM myTable),
    (SELECT gen_random_uuid())
)
```
Executing this multiple times would lead to this table:

myTable:
```
| id            | myIncrement   | other |
| ------------- |:-------------:| -----:|
| UUIDX         | 1             | 1600  |
| UUIDY         | 2             | 1600  |
| UUIDZ         | 3             | 1600  |
| UUIDQ         | 4             | 1600  |
| UUIDR         | 5             | 1600  |
| UUIDT         | 6             | 1600  |
| UUIDU         | 7             | 1600  |
| UUIDI         | 8             | 1600  |
```