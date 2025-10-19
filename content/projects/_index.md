---
title: Projects
date: 2024-05-19
type: landing

design:
  spacing: '3rem'

sections:
  - block: markdown
    content:
      title: Projects
      text: |
        <div class="projects-filter-wrapper">
          <div class="filter-buttons">
            <button class="filter-btn active" onclick="filterProjects('all')">전체</button>
            <button class="filter-btn" onclick="filterProjects('demand-modeling')">수요모델링</button>
            <button class="filter-btn" onclick="filterProjects('sales-marketing')">영업/마케팅</button>
            <button class="filter-btn" onclick="filterProjects('data-analysis')">데이터분석</button>
          </div>
        </div>
    design:
      columns: '1'
      
  - block: collection
    id: projects-grid
    content:
      title: ''
      text: ''
      filters:
        folders:
          - projects
    design:
      view: card
      columns: '3'
---

<script>
function filterProjects(category) {
  // 버튼 active 상태 변경
  document.querySelectorAll('.filter-btn').forEach(btn => {
    btn.classList.remove('active');
  });
  event.target.classList.add('active');
  
  // 카드 필터링
  const cards = document.querySelectorAll('[id="projects-grid"] article');
  
  cards.forEach(card => {
    const cardText = card.textContent.toLowerCase();
    let shouldShow = false;
    
    if (category === 'all') {
      shouldShow = true;
    } else if (category === 'demand-modeling' && cardText.includes('demand-modeling')) {
      shouldShow = true;
    } else if (category === 'sales-marketing' && cardText.includes('sales-marketing')) {
      shouldShow = true;
    } else if (category === 'data-analysis' && cardText.includes('data-analysis')) {
      shouldShow = true;
    }
    
    card.style.display = shouldShow ? 'block' : 'none';
  });
}
</script>