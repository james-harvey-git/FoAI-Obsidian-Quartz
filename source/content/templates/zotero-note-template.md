---
title: "{{ title | default('') }}"
authors: "{{ authorString | default('') }}"
year: {{ year | default('') }}
citekey: "{{ citekey | default('') }}"
zoteroKey: "{{ key | default('') }}"
---

## 🧠 Abstract
{{ abstractNote | default('') }}

## 🏷️ Tags
{% if tags and tags.length > 0 -%}
{% for t in tags -%}
- {{ t.tag }}
{% endfor -%}
{%- else -%}
- (none)
{%- endif %}

## 📑 Highlights
{% if annotations and annotations.length > 0 %}
{% for a in annotations %}
{% set highlight = a.annotatedText or a.exact or a.text or a.selectedText or a.highlightText or a.quote or a.annotationText or '' %}
{% set comment = a.comment or a.note or '' %}
{% set page = a.page or a.pageLabel or '' %}
{% set hasImage = a.imageRelativePath and (a.imageRelativePath | trim) != '' %}
{% set hasOCR = a.ocrText and (a.ocrText | trim) != '' %}
{% if highlight or comment or hasImage %}
- {{ highlight }}{% if page %} (p. {{ page }}){% endif %}{% if hasImage %}<br>![[{{ a.imageRelativePath }}]]{% if hasOCR %}<br>🔎 {{ a.ocrText | replace('\r\n', '\n') | replace('\n', '  \n') }}{% endif %}{% endif %}{% if comment and (comment | trim) != '' %}<br>💬 {{ comment | replace('\r\n', '\n') | replace('\n', '  \n') }}{% endif %}
{% endif -%}
{% endfor %}
{% else %}
_No annotations found in the Zotero PDF for this item._
{% endif %}

## 💭 My Thoughts
- 

## 🔗 Links
{% if attachments and attachments.length > 0 -%}
{%- for att in attachments | filterby('path', 'endswith', '.pdf') -%}
- [📄 PDF]({{ att.title }})
- [Local file](file://{{ att.path | replace(' ', '%20') }})
{%- endfor %}
{% endif -%}
{%- if libraryID and key -%}
- [Open Zotero Item](zotero://select/items/{{ libraryID }}_{{ key }})
{%- endif %}