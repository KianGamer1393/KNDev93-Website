<script setup>
import { RouterLink } from 'vue-router'
import InstagramButton from '../components/InstagramButton.vue'

const skills = ['Vue.js', 'JavaScript', 'Tailwind', 'Node.js', 'UI/UX', 'Vite']

const stats = [
  { value: '+۶', label: 'پروژه تکمیل‌شده' },
  { value: '+۳', label: 'سال تجربه' },
  { value: '∞', label: 'علاقه به کدنویسی' },
]

const featuredProjects = [
  {
    emoji: '📜',
    title: 'یادداشت قدیمی',
    desc: 'بازی داستانی و معمایی با فضایی نوستالژیک',
  },
  {
    emoji: '🎯',
    title: 'تپی پلن',
    desc: 'بازی استراتژی و مدیریت منابع',
  },
  {
    emoji: '🛠️',
    title: 'ZeroTools',
    desc: 'مجموعه ابزارهای آنلاین کاربردی',
  },
]
</script>

<template>
  <section class="hero container">
    <div class="hero-content">
      <span class="badge">👋 سلام، من KNDev93 هستم</span>
      <h1>
        وب‌سایت‌ها و بازی‌هایی می‌سازم که
        <span class="gradient-text">دیده می‌شن</span>
      </h1>
      <p class="hero-desc">
        توسعه‌دهنده وب و سازنده بازی با عشق به طراحی مدرن و کدهای تمیز. اینجا خونه‌ی
        پروژه‌ها و ایده‌های منه — از بازی‌های داستانی گرفته تا ابزارهای آنلاین.
      </p>
      <div class="hero-actions">
        <RouterLink to="/projects" class="btn-primary">مشاهده پروژه‌ها</RouterLink>
        <InstagramButton />
      </div>
    </div>

    <div class="hero-visual">
      <div class="glow-card">
        <div class="code-line"><span class="kw">const</span> dev = {</div>
        <div class="code-line indent">name: <span class="str">'KNDev93'</span>,</div>
        <div class="code-line indent">role: <span class="str">'Web & Game Dev'</span>,</div>
        <div class="code-line indent">passion: <span class="str">'Building cool stuff'</span></div>
        <div class="code-line">}</div>
      </div>
    </div>
  </section>

  <section class="container section">
    <h2 class="section-title">مهارت‌ها</h2>
    <div class="skill-chips">
      <span v-for="skill in skills" :key="skill" class="chip">{{ skill }}</span>
    </div>
  </section>

  <section class="container section">
    <h2 class="section-title">یک نگاه سریع</h2>
    <div class="stats-grid">
      <div v-for="stat in stats" :key="stat.label" class="stat-card">
        <span class="stat-value">{{ stat.value }}</span>
        <span class="stat-label">{{ stat.label }}</span>
      </div>
    </div>
  </section>

  <section class="container section">
    <div class="featured-header">
      <h2 class="section-title">پروژه‌های شاخص</h2>
      <RouterLink to="/projects" class="see-all">همه پروژه‌ها ←</RouterLink>
    </div>
    <div class="featured-grid">
      <RouterLink
        v-for="project in featuredProjects"
        :key="project.title"
        to="/projects"
        class="featured-card"
      >
        <span class="featured-emoji">{{ project.emoji }}</span>
        <h3>{{ project.title }}</h3>
        <p>{{ project.desc }}</p>
      </RouterLink>
    </div>
  </section>

  <section class="container section cta-section">
    <div class="cta-card">
      <h2>بیا با هم در ارتباط باشیم</h2>
      <p>آخرین پروژه‌ها و مطالب رو در اینستاگرام من دنبال کن.</p>
      <InstagramButton />
    </div>
  </section>
</template>

<style scoped>
.hero {
  display: grid;
  grid-template-columns: 1.2fr 1fr;
  gap: 60px;
  align-items: center;
  padding: 80px 24px 60px;
}

.badge {
  display: inline-block;
  padding: 6px 16px;
  background: var(--bg-soft);
  border: 1px solid var(--border);
  border-radius: 999px;
  font-size: 0.85rem;
  color: var(--text-muted);
  margin-bottom: 20px;
}

.hero h1 {
  font-size: clamp(2rem, 5vw, 3.2rem);
  line-height: 1.3;
  font-weight: 800;
  margin-bottom: 20px;
}

.gradient-text {
  background: var(--gradient);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
}

.hero-desc {
  color: var(--text-muted);
  font-size: 1.05rem;
  max-width: 480px;
  margin-bottom: 32px;
}

.hero-actions {
  display: flex;
  gap: 16px;
  flex-wrap: wrap;
}

.hero-visual {
  display: flex;
  justify-content: center;
}

.glow-card {
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: 16px;
  padding: 28px;
  font-family: 'Courier New', monospace;
  font-size: 0.95rem;
  line-height: 2;
  box-shadow: 0 0 60px rgba(124, 92, 255, 0.15);
  width: 100%;
  max-width: 360px;
  direction: ltr;
  text-align: left;
}

.code-line { color: var(--text); }
.code-line.indent { padding-left: 20px; }
.kw { color: var(--accent); }
.str { color: #7ee787; }

.section { padding: 40px 24px; }

.skill-chips {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
}

.chip {
  padding: 10px 20px;
  background: var(--bg-soft);
  border: 1px solid var(--border);
  border-radius: 10px;
  font-size: 0.9rem;
  font-weight: 500;
  transition: all 0.2s;
}

.chip:hover {
  border-color: var(--primary);
  color: var(--primary-soft);
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}

.stat-card {
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: 16px;
  padding: 32px 20px;
  text-align: center;
  display: flex;
  flex-direction: column;
  gap: 8px;
  transition: transform 0.25s, border-color 0.25s;
}

.stat-card:hover {
  transform: translateY(-4px);
  border-color: var(--primary);
}

.stat-value {
  font-size: 2.2rem;
  font-weight: 800;
  background: var(--gradient);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
}

.stat-label {
  color: var(--text-muted);
  font-size: 0.9rem;
}

.featured-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 24px;
}

.featured-header .section-title {
  margin-bottom: 0;
}

.see-all {
  color: var(--primary-soft);
  font-weight: 600;
  font-size: 0.9rem;
  transition: color 0.2s;
}

.see-all:hover { color: var(--accent); }

.featured-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}

.featured-card {
  position: relative;
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: 18px;
  padding: 32px 24px;
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
  transition: transform 0.25s, border-color 0.25s, box-shadow 0.25s;
  overflow: hidden;
}

.featured-card::before {
  content: '';
  position: absolute;
  inset: 0;
  background: radial-gradient(circle at top, rgba(124, 92, 255, 0.15), transparent 65%);
  opacity: 0;
  transition: opacity 0.3s;
  pointer-events: none;
}

.featured-card:hover {
  transform: translateY(-6px);
  border-color: var(--primary);
  box-shadow: 0 16px 40px rgba(124, 92, 255, 0.2);
}

.featured-card:hover::before { opacity: 1; }

.featured-emoji {
  font-size: 2.6rem;
  line-height: 1;
  margin-bottom: 6px;
}

.featured-card h3 {
  font-size: 1.1rem;
  font-weight: 700;
}

.featured-card p {
  color: var(--text-muted);
  font-size: 0.88rem;
}

.cta-section { padding-bottom: 80px; }

.cta-card {
  background: linear-gradient(135deg, rgba(124, 92, 255, 0.12), rgba(255, 77, 141, 0.08));
  border: 1px solid var(--border);
  border-radius: 20px;
  padding: 48px 32px;
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 16px;
}

.cta-card h2 { font-size: 1.6rem; font-weight: 800; }
.cta-card p { color: var(--text-muted); max-width: 400px; }

@media (max-width: 860px) {
  .hero {
    grid-template-columns: 1fr;
    padding-top: 48px;
    text-align: center;
  }
  .hero-desc { margin: 0 auto 32px; }
  .hero-actions { justify-content: center; }
  .stats-grid { grid-template-columns: 1fr; }
  .featured-grid { grid-template-columns: 1fr; }
  .featured-header { flex-direction: column; gap: 8px; align-items: flex-start; }
}
</style>