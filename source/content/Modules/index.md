---
type: index
module: Modules
module_tag: modules
tags:
  - index
  - modules
date: 2025-11-05
---

# Modules – Index

## 🧭 Overview
Provide a brief summary of what this module or topic covers, and how it connects to other areas.

## 📚 Contents
### 📘 Lectures
```dataview
TABLE file.link AS "Lecture Notes", date
FROM "Modules"
WHERE contains(module, this.module) AND type = "lecture"
SORT file.name ASC
```
### ### **🧩** Concepts
```dataview
TABLE file.link AS "Concept", date
FROM "Modules"
WHERE contains(module, this.module) AND type = "concept"
SORT file.name ASC
```
###  **🗂 PDFs**
```dataview
TABLE file.link AS "PDFs"
FROM "Resources/PDFs"
WHERE contains(file.name, this.module)
SORT file.name ASC
```
## **🔗 Related Modules / Topics**
- [[Modules/FoAI I - Foundational Principles/FoAI 1a Fundamental Concepts/index]]
    
- [[FoAI 1b Modern Concepts and Methods]]
    
- [[FoAI II - Modern Statistical Concepts]]
