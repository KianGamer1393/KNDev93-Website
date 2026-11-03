<script setup>
import InstagramButton from '../components/InstagramButton.vue'

const techs = [
  { name: 'Vue.js', level: 90 },
  { name: 'JavaScript', level: 88 },
  { name: 'HTML / CSS', level: 95 },
  { name: 'Node.js', level: 75 },
]

const timeline = [
  { year: '۱۴۰۰', title: 'شروع مسیر', desc: 'اولین خطوط کد و آشنایی با دنیای وب' },
  { year: '۱۴۰۱', title: 'تمرکز روی فرانت‌اند', desc: 'یادگیری Vue.js و ساخت رابط‌های مدرن' },
  { year: '۱۴۰۲', title: 'پروژه‌های واقعی', desc: 'همکاری در پروژه‌های تجاری و رشد حرفه‌ای' },
  { year: '۱۴۰۳', title: 'برند KNDev93', desc: 'ساخت هویت شخصی و اشتراک‌گذاری دانش' },
]
</script>

<template>
  <section class="container page">
    <div class="page-header">
      <span class="eyebrow">درباره من</span>
      <h1>من <span class="gradient-text">KNDev93</span> هستم</h1>
      <p class="lead">
        یه توسعه‌دهنده‌ی وب که عاشق ساختن تجربه‌های دیجیتال روان، زیبا و کاربردی هست.
        از وقتی اولین خط کد رو نوشتم، فهمیدم این مسیر همون چیزیه که می‌خوام.
      </p>
    </div>

    <div class="about-grid">
      <div class="about-card">
        <h2>داستان من</h2>
        <p>
          مسیر من از کنجکاوی نسبت به اینکه «سایت‌ها چطور کار می‌کنن» شروع شد و
          تبدیل شد به یک علاقه‌ی جدی به توسعه‌ی وب. امروز روی پروژه‌های فرانت‌اند
          با Vue.js تمرکز دارم و دوست دارم چیزهایی بسازم که هم برای کاربر لذت‌بخش
          باشن و هم از نظر فنی تمیز و اصولی.
        </p>
        <p>
          باور دارم کد خوب فقط کار نمی‌کنه، بلکه خواناست، مقیاس‌پذیره و تجربه‌ی
          کاربر رو بهتر می‌کنه. تو این مسیر، تجربه‌هام رو در اینستاگرام هم به
          اشتراک می‌ذارم.
        </p>
      </div>

      <div class="about-card">
        <h2>مهارت‌ها</h2>
        <div class="skill-list">
          <div v-for="tech in techs" :key="tech.name" class="skill-item">
            <div class="skill-head">
              <span>{{ tech.name }}</span>
              <span class="skill-percent">{{ tech.level }}%</span>
            </div>
            <div class="skill-bar">
              <div class="skill-fill" :style="{ width: tech.level + '%' }"></div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="timeline-section">
      <h2 class="section-title">مسیر من</h2>
      <div class="timeline">
        <div v-for="(item, i) in timeline" :key="i" class="timeline-item">
          <div class="timeline-dot"></div>
          <div class="timeline-body">
            <span class="timeline-year">{{ item.year }}</span>
            <h3>{{ item.title }}</h3>
            <p>{{ item.desc }}</p>
          </div>
        </div>
      </div>
    </div>

    <div class="about-cta">
      <h2>بیا در اینستاگرام هم‌مسیر بشیم</h2>
      <p>پشت‌صحنه‌ی پروژه‌ها و نکته‌های کدنویسی رو اونجا می‌ذارم.</p>
      <InstagramButton />
    </div>
  </section>
</template>

<style scoped>
.page { padding: 72px 24px 80px; }

.page-header { max-width: 720px; margin-bottom: 56px; }

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

.about-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 24px;
  margin-bottom: 64px;
}

.about-card {
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: 16px;
  padding: 32px;
}

.about-card h2 {
  font-size: 1.3rem;
  font-weight: 800;
  margin-bottom: 20px;
}

.about-card p {
  color: var(--text-muted);
  margin-bottom: 16px;
  font-size: 0.95rem;
}

.about-card p:last-child { margin-bottom: 0; }

.skill-list { display: flex; flex-direction: column; gap: 18px; }

.skill-head {
  display: flex;
  justify-content: space-between;
  font-size: 0.9rem;
  margin-bottom: 8px;
}

.skill-percent { color: var(--text-muted); }

.skill-bar {
  height: 8px;
  background: var(--bg);
  border-radius: 999px;
  overflow: hidden;
}

.skill-fill {
  height: 100%;
  background: var(--gradient);
  border-radius: 999px;
  transition: width 0.8s ease;
}

.timeline-section { margin-bottom: 64px; }

.section-title {
  font-size: 1.6rem;
  font-weight: 800;
  margin-bottom: 32px;
}

.timeline {
  display: flex;
  flex-direction: column;
  gap: 24px;
  position: relative;
  padding-right: 32px;
}

.timeline::before {
  content: '';
  position: absolute;
  right: 8px;
  top: 8px;
  bottom: 8px;
  width: 2px;
  background: var(--border);
}

.timeline-item { position: relative; }

.timeline-dot {
  position: absolute;
  right: -32px;
  top: 8px;
  width: 18px;
  height: 18px;
  border-radius: 50%;
  background: var(--gradient);
  border: 3px solid var(--bg);
}

.timeline-year {
  display: inline-block;
  font-size: 0.8rem;
  color: var(--primary-soft);
  font-weight: 700;
  margin-bottom: 4px;
}

.timeline-body h3 { font-size: 1.1rem; font-weight: 700; margin-bottom: 4px; }
.timeline-body p { color: var(--text-muted); font-size: 0.9rem; }

.about-cta {
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

.about-cta h2 { font-size: 1.4rem; font-weight: 800; }
.about-cta p { color: var(--text-muted); max-width: 400px; }

@media (max-width: 860px) {
  .about-grid { grid-template-columns: 1fr; }
}
</style>