---
type: lecture

  

<%*

const parts = tp.file.folder(true).split("/");

const i = parts.indexOf("Modules");

const after = i >= 0 ? parts.slice(i + 1) : parts;

  

const moduleName = after[0]  ?? "";

const submodule  = after[1]  ?? "";

const topicName  = after[2]  ?? parts.slice(-1)[0];

  

const slug = s => s.toLowerCase().replace(/[^a-z0-9]+/g,"-").replace(/(^-|-$)/g,"");

  

const moduleTag = slug(moduleName);

const submodTag = slug(submodule);

const topicTag  = slug(topicName);

_%>

  

module: <%* tR += moduleName %>

submodule: <%* tR += submodule %>

topic: <%* tR += topicName %>

  

module_tag: <%* tR += moduleTag %>

submodule_tag: <%* tR += submodTag %>

topic_tag: <%* tR += topicTag %>

  

date: <% tp.date.now("YYYY-MM-DD") %>

tags: [lecture, <%* tR += moduleTag %>, <%* tR += submodTag %>, <%* tR += topicTag %>]
---

# <% tp.file.title %>

![[../../../../Resources/PDFs/<% tp.file.title %>.pdf]]

## 🧭 Overview
Summarise the lecture’s focus and how it fits into *<% tp.file.folder(true).split("/").slice(-3, -2)[0] %>*.

## 🧩 Key Concepts
- [[Concept-1]]
- [[Concept-2]]

## 🧮 Core Equations
```math
% Add derivations here
```

## 💡 Insights

## ❓Questions/Gaps

## 🔗 Connections
- [[Previous Lecture]]
- [[Next Lecture]]
- [[Related Concept]]
- 