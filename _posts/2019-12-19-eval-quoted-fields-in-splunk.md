---
title: Eval quoted fields in Splunk
date: 2019-12-19
categories:
  - Blog
tags:
  - Splunk
  - Kringlecon
  - Special characters
---

### Context
Querying and using eval on complex field names in Splunk during Kringlecon 2019.

### Problem
I'd written up a query and wanted to pass a field name through the lower() function, however, the field contained special characters. Using a backslash (\) to escape these characters breaks any function you put in, and encasing the whole string in double quotes ("") passes its own value to the function. 

### Solution
Encase the field name in single quotes (''). Splunk resolves the field name and ignores any special characters, easy!

### Examples
##### Correct 
Using single quotes - returns a count of results in the specified field
```
eval loweredComplexField = lower('results{}.workers.smtp.to') | stats count by loweredComplexField
```
##### Incorrect
Using double quotes - will compile but returns the literal results{}.workers.smtp.to
```
eval loweredComplexField = lower("results{}.workers.smtp.to") | stats count by loweredComplexField
```
##### Incorrect 
Using backslash - won't compile a search
```
eval loweredComplexField = lower(results\{\}\.workers\.smtp\.to) | stats count by loweredComplexField
```
