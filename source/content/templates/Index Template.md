---
<%*
const folderPath = tp.file.folder();
const folderName = folderPath ? folderPath.split("/").pop() : "Root";
%>
title: "<% folderName %> Index"
folder: "<% folderPath %>"
created: <% tp.date.now("YYYY-MM-DD") %>
---

# <% folderName %> Index

```dataview
list
where file.folder = this.file.folder
where file.name != this.file.name
sort file.name asc
```
