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
      text: ''
    design:
      columns: '1'
---

<style>
.filter-buttons {
  display: flex;
  gap: 1rem;
  justify-content: center;
  margin: 3rem 0;
  flex-wrap: wrap;
}
.filter-btn {
  padding: 0.75rem 2rem;
  background: white;
  border: 2px solid #6366f1;
  border-radius: 50px;
  color: #6366f1;
  cursor: pointer;
  font-weight: 600;
  transition: all 0.3s ease;
  font-size: 1rem;
}
.filter-btn:hover {
  background: #eef2ff;
  transform: translateY(-2px);
}
.filter-btn.active {
  background: #6366f1;
  color: white;
}
.projects-wrapper {
  max-width: 1600px;
  margin: 0 auto;
  padding: 0 3rem;
}
.projects-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 3rem;
  margin-top: 3rem;
}
.project-card {
  border: 1px solid #e5e7eb;
  border-radius: 12px;
  overflow: hidden;
  transition: all 0.3s ease;
  background: white;
  text-decoration: none;
  color: inherit;
  display: block;
}
.project-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 30px rgba(0,0,0,0.1);
}
.project-card.hidden {
  display: none;
}
.project-image {
  width: 100%;
  height: 240px;
  object-fit: cover;
}
.project-content {
  padding: 1.5rem;
}
.project-tag {
  display: inline-block;
  padding: 0.3rem 0.85rem;
  background: #eef2ff;
  color: #6366f1;
  border-radius: 50px;
  font-size: 0.85rem;
  margin-bottom: 0.75rem;
  font-weight: 500;
}
.project-title {
  font-size: 1.4rem;
  font-weight: 700;
  margin: 0.5rem 0;
  color: #111827;
}
.project-description {
  color: #6b7280;
  margin: 0.5rem 0;
  font-size: 0.95rem;
  line-height: 1.5;
}
.project-date {
  color: #9ca3af;
  font-size: 0.85rem;
  margin-top: 0.75rem;
}
@media (max-width: 1024px) {
  .projects-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}
@media (max-width: 640px) {
  .projects-grid {
    grid-template-columns: 1fr;
  }
  .projects-wrapper {
    padding: 0 1.5rem;
  }
}
</style>

<div class="projects-wrapper">
  <div class="filter-buttons">
    <button class="filter-btn active" onclick="filterProjects('all')">전체</button>
    <button class="filter-btn" onclick="filterProjects('sales-marketing')">영업/마케팅</button>
    <button class="filter-btn" onclick="filterProjects('demand-modeling')">수요모델링</button>
    <button class="filter-btn" onclick="filterProjects('data-analysis')">데이터분석</button>
  </div>
  
  <div class="projects-grid" id="projectsGrid">
    <a href="/projects/pandas/" class="project-card" data-tags="sales-marketing data-analysis">
      <img src="/projects/pandas/featured.png" alt="영업 전환 예측" class="project-image">
      <div class="project-content">
        <span class="project-tag">영업/마케팅</span>
        <h3 class="project-title">영업 전환 예측 모델</h3>
        <p class="project-description">고객 행동 데이터 기반 전환 예측</p>
        <p class="project-date">2023년 10월</p>
      </div>
    </a>
    
    <a href="/projects/pytorch/" class="project-card" data-tags="demand-modeling data-analysis">
      <img src="/projects/pytorch/featured.png" alt="수요 예측" class="project-image">
      <div class="project-content">
        <span class="project-tag">수요모델링</span>
        <h3 class="project-title">수요 예측 모델링</h3>
        <p class="project-description">시계열 데이터 활용 수요 예측</p>
        <p class="project-date">2023년 11월</p>
      </div>
    </a>
    
    <a href="/projects/scikit/" class="project-card" data-tags="data-analysis sales-marketing">
      <img src="/projects/scikit/featured.png" alt="고객 세분화" class="project-image">
      <div class="project-content">
        <span class="project-tag">데이터 분석</span>
        <h3 class="project-title">고객 세분화 분석</h3>
        <p class="project-description">머신러닝 기반 고객 클러스터링</p>
        <p class="project-date">2023년 9월</p>
      </div>
    </a>
  </div>
</div>

<script>
function filterProjects(category) {
  document.querySelectorAll('.filter-btn').forEach(btn => {
    btn.classList.remove('active');
  });
  event.target.classList.add('active');
  const cards = document.querySelectorAll('.project-card');
  cards.forEach(card => {
    if (category === 'all') {
      card.classList.remove('hidden');
    } else {
      const tags = card.getAttribute('data-tags');
      if (tags.includes(category)) {
        card.classList.remove('hidden');
      } else {
        card.classList.add('hidden');
      }
    }
  });
}
</script>