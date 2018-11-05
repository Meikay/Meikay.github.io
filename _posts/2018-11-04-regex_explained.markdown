---
layout: post
title:      "Regex Explained"
date:       2018-11-05 04:06:12 +0000
permalink:  regex_explained
---


In a nutshell, regex is a way for you to match data using specific patterns of a string. This can be used for file renaming, validation, and searching through a database. In order to use this, we have to use `scan` and `match` ruby methods. 


The scan method returns an array of all items in the string that match the Regular Expression for example:
```
"The time I saw a mime it costed a dime".scan(/\w+ime/)
=> ["time", "mime", "dime"]
```


The match method returns the first item in your string that matches a given Regular Expression for example:
```
"The time I saw a mime it cost a dime".match(/\w+ime/)
=> ["time"]
```


Grep is an enumerable method for pattern searching in arrays and hashes.

```
names = ["Anna Garcia, Emily Blank, Brian Pilozzi, Suzan Nora, Jimmy Halt, John Pate"]

#Get items from array where first name has five letters:
names.grep(/^\w{5}\s/)

=>["Emily Blank", "Brian Pilozzi", "Suzan Nora", "Jimmy Halt"]
```
