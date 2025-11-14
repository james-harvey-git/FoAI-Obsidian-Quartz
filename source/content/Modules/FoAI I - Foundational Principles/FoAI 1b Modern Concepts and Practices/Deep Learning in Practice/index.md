---
type: index
module: FoAI I - Foundational Principles
submodule: FoAI 1b Modern Concepts and Practices
topic: Deep Learning in Practice
module_tag: foai-i-foundational-principles
submodule_tag: foai-1b-modern-concepts-and-practices
topic_tag: deep-learning-in-practice
tags:
  - index
  - foai-i-foundational-principles
  - foai-1b-modern-concepts-and-practices
  - deep-learning-in-practice
date: 2025-11-05
---

  

# index – Index

  

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
