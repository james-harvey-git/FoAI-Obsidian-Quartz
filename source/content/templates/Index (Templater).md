---

<%*

const parts = tp.file.folder(true).split("/");

const i = parts.indexOf("Modules");           // find the root

const after = i >= 0 ? parts.slice(i + 1) : parts;

  

// after[0] = FoAI I - Foundational Principles

// after[1] = FoAI 1b Modern Concepts and...

// after[2] = Deep Learning in Practice  (this folder)

  

const moduleName   = after[0]  ?? "";

const submodule    = after[1]  ?? "";

const topicName    = after[2]  ?? parts.slice(-1)[0];

  

const slug = s => s.toLowerCase().replace(/[^a-z0-9]+/g,"-").replace(/(^-|-$)/g,"");

const moduleTag  = slug(moduleName);

const submodTag  = slug(submodule);

const topicTag   = slug(topicName);

_%>

type: index

module: <%* tR += moduleName %>

submodule: <%* tR += submodule %>

topic: <%* tR += topicName %>

module_tag: <%* tR += moduleTag %>

submodule_tag: <%* tR += submodTag %>

topic_tag: <%* tR += topicTag %>

tags: [index, <%* tR += moduleTag %>, <%* tR += submodTag %>, <%* tR += topicTag %>]

date: <% tp.date.now("YYYY-MM-DD") %>

---

  

# <% tp.file.title %> – Index

  

## 🧭 Overview

Provide a brief summary of what this module or topic covers, and how it connects to other areas.

  

## 📚 Contents

  

### 📘 Lectures

```dataview

TABLE file.link AS "Lecture Notes", date

FROM "Modules"

WHERE type = "lecture" AND topic_tag = this.topic_tag

SORT file.name ASC
```

### **🧩 Concepts**
```dataview
TABLE file.link AS "Concept", date
FROM "Modules"
WHERE type = "concept" AND topic_tag = this.topic_tag
SORT file.name ASC
```
