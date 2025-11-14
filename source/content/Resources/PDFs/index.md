---

type: index

category: PDFs

tags: [index, resources, pdfs]

---

  

# 📚 PDF Library Index

  

## 🧭 Overview

This index lists all lecture slides and readings stored in `/Resources/PDFs`.  

Click a link to preview or embed any file in your notes.

  

---

  

### 📘 All PDFs

```dataview
TABLE file.name AS "File", file.link AS "PDF File", file.mtime AS "Last Modified"

FROM "Resources/PDFs"

WHERE file.ext = "pdf"

SORT file.name ASC
```
