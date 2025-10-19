---
title: 'Projects'
date: 2024-05-19
type: landing

design:
  # Section spacing
  spacing: '5rem'

# Page sections
sections:
  - block: portfolio
    content:
      title: Projects
      text: I enjoy making things. Here are a selection of projects that I have worked on over the years.
      
      # 1. 필터 기준 설정
      filter_by: "tags"
      
      # 2. (추가!) 필터 버튼 '켜기'
      show_filter_categories: true 
      
      # 3. 필터 스타일 설정
      filter_style: "navbar"
      
      # (이 부분은 올바르게 잘 하셨습니다)
      filters:
        folders:
          - projects
    design:
      view: acard
      fill_image: false
      columns: 4
      show_date: false
      show_read_time: false
      show_read_more: false
---