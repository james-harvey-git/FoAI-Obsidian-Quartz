---

<%*

const folderPath = tp.file.folder();          // e.g. "AI/Foundations/Week 1"

  

const folderName = folderPath.split("/").pop(); // e.g. "Week 1"

  


_%>

title: "<%= folderName %> Index"

  

folder: "<%= folderPath %>"

  

created: <% tp.date.now("YYYY-MM-DD") %>

---

  

# <%= folderName %> Index

  
```dataview

  

list from "<%= folderPath %>"

  

where file.name != this.file.name

  

sort file.name asc

```