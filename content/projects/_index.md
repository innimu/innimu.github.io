---
title: Projects
date: 2024-05-19
type: landing

sections:
  - block: markdown
    content:
      title: Projects
      subtitle: 전체 영업/마케팅 수요모델링 데이터 분석
      text: |
        <style>
        .filter-buttons {
          display: flex;
          gap: 1rem;
          justify-content: center;
          margin: 2rem 0;
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
        .projects-grid {
          display: grid;
          grid-template-columns: repeat(3, 1fr);
          gap: 2rem;
          margin-top: 3rem;
        }
        .project-card {
          border: 1px solid #e5e7eb;
          border-radius: 12px;
          overflow: hidden;
          transition: all 0.3s ease;
          background: white;
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
          height: 200px;
          object-fit: cover;
        }
        .project-content {
          padding: 1.5rem;
        }
        .project-tag {
          display: inline-block;
          padding: 0.25rem 0.75rem;
          background: #eef2ff;
          color: #6366f1;
          border-radius: 50px;
          font-size: 0.875rem;
          margin-bottom: 0.5rem;
        }
        .project-title {
          font-size: 1.5rem;
          font-weight: 700;
          margin: 0.5rem 0;
          color: #111827;
        }
        .project-description {
          color: #6b7280;
          margin: 0.5rem 0;
        }
        .project-date {
          color: #9ca3af;
          font-size: 0.875rem;
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
        }
        </style>
        
        <div class="filter-buttons">
          <button class="filter-btn active" onclick="filterProjects('all')">전체</button>
          <button class="filter-btn" onclick="filterProjects('sales-marketing')">영업/마케팅</button>
          <button class="filter-btn" onclick="filterProjects('demand-modeling')">수요모델링</button>
          <button class="filter-btn" onclick="filterProjects('data-analysis')">데이터 분석</button>
        </div>
        
        <div class="projects-grid" id="projectsGrid">
          <!-- 프로젝트 1 -->
          <div class="project-card" data-tags="sales-marketing data-analysis">
            <img src="/projects/pandas/featured.png" alt="프로젝트" class="project-image">
            <div class="project-content">
              <span class="project-tag">영업/마케팅</span>
              <h3 class="project-title">영업 전환 예측 모델</h3>
              <p class="project-description">고객 행동 데이터를 기반으로 영업 전환 가능성을 예측</p>
              <p class="project-date">2023년 10월</p>
            </div>
          </div>
          
          <!-- 프로젝트 2 -->
          <div class="project-card" data-tags="demand-modeling data-analysis">
            <img src="/projects/pytorch/featured.png" alt="프로젝트" class="project-image">
            <div class="project-content">
              <span class="project-tag">수요모델링</span>
              <h3 class="project-title">수요 예측 모델링</h3>
              <p class="project-description">시계열 데이터를 활용한 수요 예측 딥러닝 모델</p>
              <p class="project-date">2023년 11월</p>
            </div>
          </div>
          
          <!-- 프로젝트 3 -->
          <div class="project-card" data-tags="data-analysis sales-marketing">
            <img src="/projects/scikit/featured.png" alt="프로젝트" class="project-image">
            <div class="project-content">
              <span class="project-tag">데이터 분석</span>
              <h3 class="project-title">고객 세분화 분석</h3>
              <p class="project-description">머신러닝 기반 고객 클러스터링 프로젝트</p>
              <p class="project-date">2023년 9월</p>
            </div>
          </div>
        </div>
        
        <script>
        function filterProjects(category) {
          // 모든 버튼에서 active 제거
          document.querySelectorAll('.filter-btn').forEach(btn => {
            btn.classList.remove('active');
          });
          
          // 클릭된 버튼에 active 추가
          event.target.classList.add('active');
          
          // 모든 카드 가져오기
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
---