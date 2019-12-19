---
title: Parse an XML file into a variable with Powershell
categories:
  - Blog
tags:
  - XML
  - Powershell
  - Kringlecon
---
### Context
Requirement to parse XML, identify a field and count its occurances during Kringlecon 2019.

### Problem
Parse the XML, access fields and count them.

### Solution
Read the file with Get-Content and assign to a variable casted to [xml] type.

### Examples
Read the file and parse as XML into a variable named $cn.
```
[xml]$cn = Get-Content filename-here.xml
```
Discover the structure of the variable, tab completion works.
```
$cn.Object.SubObject.SubSubObject
```
Sort or group by a specified property/object.
```
$cn.Object | Group-Object -Property SubObject
```
