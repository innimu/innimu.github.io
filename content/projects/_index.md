---
title: Projects
date: 2024-05-19
type: landing

design:
  spacing: '3rem'

sections:
  - block: markdown
    content:
      title: ''
      text: '{{ partial "projects-filter.html" . }}'
    design:
      columns: '1'
      
  - block: collection
    content:
      title: Projects
      text: ''
      filters:
        folders:
          - projects
    design:
      view: card
      columns: '3'
---