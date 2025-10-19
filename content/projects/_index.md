---
title: 'Projects'
date: 2024-05-19
type: landing

design:
  spacing: '5rem'

sections:
  - block: collection
    content:
      title: Projects
      subtitle: ''
      text: I enjoy making things. Here are a selection of projects that I have worked on over the years.
      
      # 프로젝트 폴더에서 콘텐츠 가져오기
      filters:
        folders:
          - projects
        exclude_featured: false
      
      # 태그별 필터 버튼 (카테고리처럼 작동)
      filter_button:
        - name: All
          tag: '*'
        - name: 영업/마케팅
          tag: sales-marketing
        - name: 수요모델링
          tag: demand-modeling
        - name: 데이터 분석
          tag: data-analysis
        - name: Python
          tag: Python
        
    design:
      view: card
      columns: '3'
---