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
      
      count: 0  # 모든 프로젝트 표시
      offset: 0
      order: desc
      
      filters:
        folders:
          - projects
        exclude_featured: false
        exclude_past: false
        exclude_future: false
        
      # 태그 필터 활성화
      filter_default: 0
      filter_button:
        - name: 전체
          tag: '*'
        - name: 영업/마케팅
          tag: sales-marketing
        - name: 수요모델링
          tag: demand-modeling
        - name: 데이터 분석
          tag: data-analysis
        
    design:
      view: showcase  # 또는 compact, card 시도
      columns: '2'
      flip_alt_rows: false