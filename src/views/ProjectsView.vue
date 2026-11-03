<script setup>
import { ref, computed } from 'vue'
import InstagramButton from '../components/InstagramButton.vue'
import GameModal from '../components/GameModal.vue'

const projects = ref([
  {
    title: 'یادداشت قدیمی',
    desc: 'یک بازی داستانی و معمایی با فضایی نوستالژیک. بازیکن با کشف سرنخ‌ها و حل معماها، رازهای یک یادداشت قدیمی رو کشف می‌کنه.',
    tags: ['بازی', 'داستانی', 'معمایی'],
    category: 'بازی',
    link: 'https://myket.ir/app/com.zerostudio.yaddasht',
    embedUrl: 'https://myket.ir/app/com.zerostudio.yaddasht',
    featured: true,
    emoji: '📜',
  },
  {
    title: 'تپی پلن',
    desc: 'یک بازی مبتنی بر مدیریت و برنامه‌ریزی. بازیکن باید با استراتژی درست، منابع و زمان رو مدیریت کنه تا به هدف برسه.',
    tags: ['بازی', 'استراتژی', 'مدیریتی'],
    category: 'بازی',
    link: 'https://cafebazaar.ir/app/com.zerostudio.tappy',
    embedUrl: 'https://cafebazaar.ir/app/com.zerostudio.tappy',
    featured: true,
    emoji: '🎯',
  },
  {
    title: 'وب‌سایت ZeroTools',
    desc: 'مجموعه‌ای از ابزارهای آنلاین کاربردی در یک وب‌سایت مدرن. طراحی مینیمال، سریع و کاربرپسند با تمرکز روی تجربه‌ی کاربری.',
    tags: ['Vue.js', 'ابزار آنلاین', 'وب‌سایت'],
    category: 'وب‌سایت',
    link: 'https://zerotools.ir',
    embedUrl: '',
    featured: true,
    emoji: '🛠️',
  },
])

const categories = computed(() => ['همه', ...new Set(projects.value.map((p) => p.category))])
const activeCategory = ref('همه')
const selectedProject = ref(null)

const filteredProjects = computed(() => {
  if (activeCategory.value === 'همه') return projects.value
  return projects.value.filter((p) => p.category === activeCategory.value)
})

function openProject(project) {
  if (project.embedUrl) {
    selectedProject.value = project
  } else {
    window.open(project.link, '_blank', 'noopener')
  }
}
</script>

<template>
  <section class="container page">
    <div class="page-header">
      <span class="eyebrow">نمونه‌کارها</span>
      <h1>پروژه‌های <span class="gradient-text">من</span></h1>
      <p class="lead">
        مجموعه‌ای از بازی‌ها و وب‌سایت‌هایی که ساختم. روی هر کارت کلیک کن تا
        مستقیم داخل سایت ببینیش!
      </p>
    </div>

    <div class="filters">
      <button
        v-for="cat in categories"
        :key="cat"
        :class="['filter-btn', { active: activeCategory === cat }]"
        @click="activeCategory = cat"
      >
        {{ cat }}
      </button>
    </div>

    <div class="projects-grid">
      <article
        v-for="(project, i) in filteredProjects"
        :key="project.title"
        :class="['project-card', { featured: project.featured }]"
        :style="{ animationDelay: i * 80 + 'ms' }"
        @click="openProject(project)"
      >
        <div class="card-top">
          <span class="project-emoji">{{ project.emoji }}</span>
          <span class="project-badge">{{ project.category }}</span>
        </div>
        <h2>{{ project.title }}</h2>
        <p>{{ project.desc }}</p>
        <div class="project-tags">
          <span v-for="tag in project.tags" :key="tag" class="tag">{{ tag }}</span>
        </div>
        <div class="card-actions">
          <button
            v-if="project.embedUrl"
            class="project-link play-btn"
            @click.stop="openProject(project)"
          >
            ▶ بازی کن
          </button>
          <a
            :href="project.link"
            target="_blank"
            rel="noopener noreferrer"
            class="project-link"
            @click.stop
          >
            باز کردن ↗
          </a>
        </div>
      </article>
    </div>

    <div class="projects-cta">
      <h2>پروژه‌های بیشتر توی اینستاگرام</h2>
      <p>کارهای جدید و پشت‌صحنه‌ی ساختشون رو اونجا می‌ذارم.</p>
      <InstagramButton />
    </div>
  </section>

  <GameModal
    v-if="selectedProject"
    :project="selectedProject"
    @close="selectedProject = null"
  />
</template>

<style scoped>
.page { padding: 72px 24px 80px; }

.page-header { max-width: 720px; margin-bottom: 40px; }

.eyebrow {
  display: inline-block;
  font-size: 0.85rem;
  font-weight: 700;
  color: var(--primary-soft);
  letter-spacing: 1px;
  margin-bottom: 12px;
}

.page-header h1 {
  font-size: clamp(2rem, 4vw, 2.8rem);
  font-weight: 800;
  margin-bottom: 20px;
}

.gradient-text {
  background: var(--gradient);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
}

.lead { color: var(--text-muted); font-size: 1.1rem; }

.filters {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-bottom: 36px;
}

.filter-btn {
  padding: 8px 18px;
  background: var(--bg-soft);
  border: 1px solid var(--border);
  color: var(--text-muted);
  border-radius: 999px;
  cursor: pointer;
  font-family: inherit;
  font-size: 0.88rem;
  transition: all 0.2s;
}

.filter-btn:hover {
  border-color: var(--primary);
  color: var(--text);
}

.filter-btn.active {
  background: var(--gradient);
  border-color: transparent;
  color: #fff;
  font-weight: 700;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
  gap: 24px;
  margin-bottom: 64px;
}

.project-card {
  position: relative;
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: 18px;
  padding: 28px;
  display: flex;
  flex-direction: column;
  gap: 14px;
  transition: transform 0.25s, border-color 0.25s, box-shadow 0.25s;
  animation: fadeUp 0.4s ease both;
  overflow: hidden;
  cursor: pointer;
}

.project-card::before {
  content: '';
  position: absolute;
  inset: 0;
  background: radial-gradient(circle at top right, rgba(124, 92, 255, 0.15), transparent 60%);
  opacity: 0;
  transition: opacity 0.3s;
  pointer-events: none;
}

.project-card:hover {
  transform: translateY(-6px);
  border-color: var(--primary);
  box-shadow: 0 16px 40px rgba(124, 92, 255, 0.2);
}

.project-card:hover::before { opacity: 1; }

.project-card.featured {
  border-color: rgba(124, 92, 255, 0.4);
}

@keyframes fadeUp {
  from { opacity: 0; transform: translateY(16px); }
  to { opacity: 1; transform: translateY(0); }
}

.card-top {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.project-emoji {
  font-size: 2rem;
  line-height: 1;
}

.project-badge {
  display: inline-block;
  font-size: 0.75rem;
  padding: 4px 12px;
  border-radius: 999px;
  background: rgba(124, 92, 255, 0.15);
  color: var(--primary-soft);
  font-weight: 600;
}

.project-card h2 {
  font-size: 1.2rem;
  font-weight: 700;
}

.project-card p {
  color: var(--text-muted);
  font-size: 0.92rem;
  flex: 1;
  line-height: 1.9;
}

.project-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
}

.tag {
  font-size: 0.75rem;
  padding: 3px 10px;
  background: var(--bg);
  border: 1px solid var(--border);
  border-radius: 6px;
  color: var(--text-muted);
}

.card-actions {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  margin-top: 8px;
}

.project-link {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  color: var(--primary-soft);
  font-weight: 600;
  font-size: 0.9rem;
  transition: color 0.2s;
  background: none;
  border: none;
  cursor: pointer;
  font-family: inherit;
  padding: 0;
}

.project-link:hover { color: var(--accent); }

.play-btn {
  padding: 8px 18px;
  background: var(--gradient);
  color: #fff !important;
  border-radius: 10px;
}

.play-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 20px rgba(124, 92, 255, 0.4);
}

.projects-cta {
  background: linear-gradient(135deg, rgba(124, 92, 255, 0.12), rgba(255, 77, 141, 0.08));
  border: 1px solid var(--border);
  border-radius: 20px;
  padding: 40px 32px;
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 14px;
}

.projects-cta h2 { font-size: 1.4rem; font-weight: 800; }
.projects-cta p { color: var(--text-muted); max-width: 400px; }

@media (max-width: 600px) {
  .projects-grid { grid-template-columns: 1fr; }
}
</style>