---
title: Projects
type: landing

sections:
  - block: markdown
    content:
      text: |
        <style>
          .filter-bar{
            display:flex;
            gap:.75rem;
            flex-wrap:wrap;
            justify-content:center;
            margin:0.5rem 0 0.5rem;
          }
          .filter-btn{
            padding:.55rem 1.1rem;
            border:2px solid #635bff;
            border-radius:999px;
            background:#fff;
            color:#635bff;
            font-weight:650;
            cursor:pointer;
            transition:.2s;
          }
          .filter-btn:hover{background:#eef2ff}
          .filter-btn.active{background:#635bff;color:#fff}
          .filter-note{
            font-size:.9rem;
            color:#6b7280;
            text-align:center;
            margin-top:.25rem;
            margin-bottom:1.5rem;
          }
          
          #project-collection > div:first-child {
            margin-bottom: 0 !important;
            padding-bottom: 0.5rem !important;
          }
          
          #project-collection .grid,
          #project-collection .hb-section-content,
          #project-collection .hbx-section-content {
            display: grid !important;
            grid-template-columns: repeat(3, minmax(0, 1fr)) !important;
            gap: 2.5rem !important;
            max-width: 1600px !important;
            margin: 0 auto !important;
            padding: 0 9rem !important;
            margin-top: 1rem !important;
          }
          
          #project-collection .grid > *,
          #project-collection .hb-section-content > *,
          #project-collection .hbx-section-content > * {
            width: 100% !important;
          }
          
          @media (max-width: 1024px) {
            #project-collection .grid,
            #project-collection .hb-section-content,
            #project-collection .hbx-section-content {
              grid-template-columns: repeat(2, minmax(0, 1fr)) !important;
              gap: 2rem !important;
            }
          }
          
          @media (max-width: 640px) {
            #project-collection .grid,
            #project-collection .hb-section-content,
            #project-collection .hbx-section-content {
              grid-template-columns: 1fr !important;
              gap: 1.5rem !important;
              padding: 0 1rem !important;
            }
          }
        </style>

        <div class="filter-bar" id="projectFilterBar">
          <button type="button" class="filter-btn active" data-filter="*">ALL</button>
          <button type="button" class="filter-btn" data-filter="sales-marketing">Sales/Marketing</button>
          <button type="button" class="filter-btn" data-filter="industrial-ai">Industrial AI</button>
          <button type="button" class="filter-btn" data-filter="generative-ai">Generative AI</button>
          <button type="button" class="filter-btn" data-filter="data-eng">Data Engineering</button>
        </div>
        <div class="filter-note">🔅카테고리 버튼을 눌러보세요🔅</div>

  - block: collection
    id: project-collection
    content:
      title: Projects
      subtitle: 영업/마케팅 · 산업 AI · 생성형 AI · 데이터 분석
      filters:
        folders: ["projects"]
      count: 30
      sort_by: date
      order: desc
      fields: ["image", "title", "description", "tags", "date"]
      show_meta: true
      show_taxonomies: true
    design:
      columns: 3
      view: card
      image_ratio: "16:9"

  - block: markdown
    content:
      text: |
        <script>
        (function(){
          console.log('🚀 필터 스크립트 초기화');
          
          const normalizeTag = (tag) => {
            return tag.toLowerCase()
              .replace(/[^\wㄱ-힣]/g, '-')
              .replace(/-+/g, '-')
              .replace(/^-|-$/g, '');
          };

          const getItems = () => {
            const container = document.getElementById('project-collection');
            if (!container) {
              console.warn('⚠️ project-collection을 찾을 수 없습니다');
              return [];
            }

            const selectors = [
              '#project-collection .grid > *',
              '#project-collection .hb-section-content > *',
              '#project-collection .hbx-section-content > *',
              '#project-collection [role="article"]',
              '#project-collection .card',
              '#project-collection .hb-card'
            ];

            for (const selector of selectors) {
              const items = document.querySelectorAll(selector);
              if (items.length > 0) {
                console.log(`✅ ${items.length}개 아이템 발견 (${selector})`);
                return Array.from(items);
              }
            }

            console.warn('⚠️ 프로젝트 아이템을 찾을 수 없습니다');
            return [];
          };

          const projectTagsMap = {
            "광고 클릭 예측 모델 (Toss NEXT ML CHALLENGE)": ["sales-marketing"],
            "베이즈 기반 인과추론 (Uplift Modeling)": ["sales-marketing"],
            "멀티모달 추천시스템 (인하 AI 챌린지)": ["sales-marketing"],
            "열판매 수요 예측": ["industrial-ai"],
            "엔진 이상 탐지": ["industrial-ai"],
            "옥수수 수율 예측": ["industrial-ai"],
            "DTAQ: 데이터 품질 평가": ["generative-ai"],
            "이미지 색채화 (Diffusion)": ["generative-ai"],
            "데이터 운영·자동화 담당": ["data-eng"],
            "위해 기체 정밀 분석 DB 관리 프로그램 구축": ["data-eng"]
          };

          const extractTags = (item) => {
            const tags = new Set();

            const titleEl = item.querySelector('h3, .hb-card-title, [id^="card-title"]');
            if (titleEl) {
              const title = titleEl.textContent.trim();
              
              if (projectTagsMap[title]) {
                projectTagsMap[title].forEach(tag => {
                  tags.add(tag);
                  console.log(`  🎯 매핑된 태그: ${tag} (제목: "${title}")`);
                });
              } else {
                for (const [mappedTitle, mappedTags] of Object.entries(projectTagsMap)) {
                  if (title.includes(mappedTitle) || mappedTitle.includes(title)) {
                    mappedTags.forEach(tag => {
                      tags.add(tag);
                      console.log(`  🎯 부분 매칭 태그: ${tag} (제목: "${title}")`);
                    });
                    break;
                  }
                }
              }
            }

            const tagLinks = item.querySelectorAll('a[href*="/tags/"]');
            tagLinks.forEach(link => {
              const href = link.getAttribute('href');
              const match = href.match(/\/tags\/([^\/]+)/);
              if (match) {
                tags.add(match[1]);
                console.log(`  🏷️ Hugo 태그: ${match[1]}`);
              }
            });

            const badges = item.querySelectorAll('.inline-flex.items-center, .badge, .hb-badge');
            badges.forEach(badge => {
              const text = badge.textContent.trim();
              if (text) {
                const normalized = normalizeTag(text);
                tags.add(normalized);
                console.log(`  🏷️ 배지 태그: ${text} → ${normalized}`);
              }
            });

            return Array.from(tags);
          };

          const hydrateItems = () => {
            const items = getItems();
            console.log(`📄 ${items.length}개 아이템 처리 중...`);
            
            items.forEach((item, index) => {
              const tags = extractTags(item);
              if (tags.length > 0) {
                item.setAttribute('data-tags', tags.join(','));
                console.log(`✅ 아이템 ${index}: data-tags="${tags.join(',')}"`);
              } else {
                console.log(`⚠️ 아이템 ${index}: 태그 없음`);
              }
            });

            return items;
          };

          const filterItems = (filterKey) => {
            console.log(`\n🎯 필터 적용: ${filterKey}`);
            const items = getItems();
            let visibleCount = 0;

            items.forEach((item, index) => {
              const dataTags = item.getAttribute('data-tags');
              
              if (filterKey === '*') {
                item.style.display = '';
                visibleCount++;
              } else {
                if (dataTags && dataTags.split(',').includes(filterKey)) {
                  item.style.display = '';
                  visibleCount++;
                  console.log(`  ✅ 아이템 ${index} 표시 (tags: ${dataTags})`);
                } else {
                  item.style.display = 'none';
                  console.log(`  ❌ 아이템 ${index} 숨김 (tags: ${dataTags})`);
                }
              }
            });

            console.log(`\n👁️ 표시된 아이템: ${visibleCount}/${items.length}\n`);
          };

          const setupButtons = () => {
            const bar = document.getElementById('projectFilterBar');
            if (!bar) {
              console.warn('⚠️ 필터 버튼 바를 찾을 수 없습니다');
              return;
            }

            bar.addEventListener('click', (e) => {
              const btn = e.target.closest('.filter-btn');
              if (!btn) return;

              console.log('\n' + '='.repeat(50));
              console.log(`🖱️ 버튼 클릭: ${btn.textContent}`);
              console.log('='.repeat(50));

              bar.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
              btn.classList.add('active');

              const filterKey = btn.getAttribute('data-filter');
              filterItems(filterKey);
            });

            console.log('✅ 버튼 이벤트 설정 완료');
          };

          const init = () => {
            console.log('\n' + '='.repeat(50));
            console.log('🎬 필터 시스템 초기화 시작');
            console.log('='.repeat(50) + '\n');
            
            hydrateItems();
            setupButtons();
            
            console.log('\n✅ 초기화 완료!\n');
          };

          if (document.readyState === 'loading') {
            document.addEventListener('DOMContentLoaded', () => {
              setTimeout(init, 200);
            });
          } else {
            setTimeout(init, 200);
          }

          let initTimeout;
          const observer = new MutationObserver(() => {
            clearTimeout(initTimeout);
            initTimeout = setTimeout(() => {
              const items = getItems();
              if (items.length > 0 && !items[0].hasAttribute('data-tags')) {
                console.log('📄 DOM 변경 감지 - 재초기화');
                hydrateItems();
              }
            }, 300);
          });

          observer.observe(document.body, {
            childList: true,
            subtree: true
          });

        })();

        (function(){
          const adjustSpacing = () => {
            const filterSection = document.querySelector('section:has(#projectFilterBar)');
            if (filterSection) {
              filterSection.style.paddingTop = '2rem';
              filterSection.style.paddingBottom = '1rem';
              console.log('✅ 필터 섹션 여백 조정됨');
            }

            const projectSection = document.getElementById('project-collection');
            if (projectSection) {
              projectSection.style.paddingTop = '1rem';
              console.log('✅ Projects 섹션 여백 조정됨');
            }
          };

          if (document.readyState === 'loading') {
            document.addEventListener('DOMContentLoaded', adjustSpacing);
          } else {
            adjustSpacing();
          }

          setTimeout(adjustSpacing, 100);
          setTimeout(adjustSpacing, 300);
          setTimeout(adjustSpacing, 500);
        })();
        </script>
---