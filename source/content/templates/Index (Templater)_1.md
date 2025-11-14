---
type: index
module: <% tp.file.folder(true).split("/").slice(-1)[0] %>
module_tag: <% tp.file.folder(true).split("/").slice(-1)[0].toLowerCase().replace(/[^a-z0-9]+/g,"-").replace(/(^-|-$)/g,"") %>
tags: [index, <% tp.file.folder(true).split("/").slice(-1)[0].toLowerCase().replace(/[^a-z0-9]+/g,"-").replace(/(^-|-$)/g,"") %>]
date: <% tp.date.now("YYYY-MM-DD") %>
---

# <% tp.file.folder(true).split("/").slice(-1)[0] %> – Index

## 🧭 Overview
Provide a brief summary of what this module or topic covers, and how it connects to other areas.

## 📚 Contents

```dataview
TABLE file.link AS "Concept", date
FROM "Modules"
WHERE contains(module, this.module) AND type = "concept"
SORT file.name ASC
```

## **🔗 Related Modules / Topics**
