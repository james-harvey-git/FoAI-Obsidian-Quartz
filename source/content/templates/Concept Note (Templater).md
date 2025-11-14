---

---
---
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

type: concept

  

module: <%* tR += moduleName %>

  

submodule: <%* tR += submodule %>

  

topic: <%* tR += topicName %>

  

module_tag: <%* tR += moduleTag %>

  

submodule_tag: <%* tR += submodTag %>

  

topic_tag: <%* tR += topicTag %>

  

date: <% tp.date.now("YYYY-MM-DD") %>

  

tags: [concept, <%* tR += moduleTag %>, <%* tR += submodTag %>, <%* tR += topicTag %>]

---



# <% tp.file.title %>

> [!note] Definition
> Write the formal or intuitive definition of the concept.

> [!tip] Intuition
> Summarise the underlying intuition, analogy, or key takeaway.

> [!example] Example / Application
> 

> [!link] Related
> - [[Lecture Overview]]
> - [[Another Concept]]


## 🧮 Key Equations
```math
% Add equations or derivations here
```

## 💡 Insights

## ❓Questions/Gaps
