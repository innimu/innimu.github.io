---
title: 'Projects'
date: 2024-05-19
type: landing

design:
  spacing: '5rem'

sections:
  - block: markdown
    content:
      title: Projects
      text: |
        <div class="project-filter-buttons">
          <button class="filter-btn active" data-filter="all">전체</button>
          <button class="filter-btn" data-filter="sales-marketing">영업/마케팅</button>
          <button class="filter-btn" data-filter="demand-modeling">수요모델링</button>
          <button class="filter-btn" data-filter="data-analysis">데이터 분석</button>
        </div>
        
  - block: collection
    content:
      filters:
        folders:
          - projects
    design:
      view: card
      columns: '3'
---