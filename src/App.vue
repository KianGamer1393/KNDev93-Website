<script setup>
import { ref } from 'vue'
import { RouterLink, RouterView } from 'vue-router'
import InstagramButton from './components/InstagramButton.vue'

const menuOpen = ref(false)

const links = [
  { to: '/', label: 'خانه' },
  { to: '/about', label: 'درباره من' },
  { to: '/projects', label: 'پروژه‌ها' },
]
</script>

<template>
  <header class="site-header">
    <div class="container header-inner">
      <RouterLink to="/" class="logo">
        <span class="logo-mark">KN</span>
        <span class="logo-text">Dev<strong>93</strong></span>
      </RouterLink>

      <nav :class="['nav', { open: menuOpen }]">
        <RouterLink
          v-for="link in links"
          :key="link.to"
          :to="link.to"
          class="nav-link"
          @click="menuOpen = false"
        >
          {{ link.label }}
        </RouterLink>
      </nav>

      <div class="header-actions">
        <InstagramButton size="small" />
        <button class="menu-toggle" @click="menuOpen = !menuOpen" aria-label="منو">
          <span></span><span></span><span></span>
        </button>
      </div>
    </div>
  </header>

  <main class="site-main">
    <RouterView v-slot="{ Component }">
      <Transition name="fade" mode="out-in">
        <component :is="Component" />
      </Transition>
    </RouterView>
  </main>

  <footer class="site-footer">
    <div class="container footer-inner">
      <div class="footer-brand">
        <span class="logo-mark">KN</span>
        <p>ساخته‌شده با ❤️ توسط KNDev93</p>
      </div>
      <div class="footer-social">
        <InstagramButton />
      </div>
      <p class="copyright">
        © {{ new Date().getFullYear() }} KNDev93 — تمامی حقوق محفوظ است.
      </p>
    </div>
  </footer>
</template>

<style scoped>
.site-header {
  position: sticky;
  top: 0;
  z-index: 50;
  backdrop-filter: blur(16px);
  background: rgba(10, 10, 15, 0.75);
  border-bottom: 1px solid var(--border);
}

.header-inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 72px;
}

.logo {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 1.25rem;
  font-weight: 800;
}

.logo-mark {
  display: inline-grid;
  place-items: center;
  width: 40px;
  height: 40px;
  border-radius: 12px;
  background: var(--gradient);
  color: #fff;
  font-size: 0.9rem;
  font-weight: 800;
}

.logo-text strong {
  background: var(--gradient);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
}

.nav {
  display: flex;
  gap: 8px;
}

.nav-link {
  padding: 8px 16px;
  border-radius: 8px;
  color: var(--text-muted);
  font-weight: 500;
  transition: all 0.2s;
}

.nav-link:hover,
.nav-link.router-link-active {
  color: var(--text);
  background: var(--bg-soft);
}

.header-actions {
  display: flex;
  align-items: center;
  gap: 12px;
}

.menu-toggle {
  display: none;
  flex-direction: column;
  gap: 4px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 8px;
}

.menu-toggle span {
  display: block;
  width: 22px;
  height: 2px;
  background: var(--text);
  border-radius: 2px;
}

.site-main {
  min-height: calc(100vh - 72px - 220px);
}

.site-footer {
  border-top: 1px solid var(--border);
  padding: 48px 0 32px;
  margin-top: 80px;
  background: var(--bg-soft);
}

.footer-inner {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
  text-align: center;
}

.footer-brand {
  display: flex;
  align-items: center;
  gap: 12px;
}

.footer-brand p {
  color: var(--text-muted);
  font-size: 0.9rem;
}

.copyright {
  color: var(--text-muted);
  font-size: 0.85rem;
  padding-top: 16px;
  border-top: 1px solid var(--border);
  width: 100%;
}

@media (max-width: 768px) {
  .nav {
    position: absolute;
    top: 72px;
    right: 0;
    left: 0;
    flex-direction: column;
    background: var(--bg-soft);
    border-bottom: 1px solid var(--border);
    padding: 16px;
    transform: translateY(-120%);
    opacity: 0;
    pointer-events: none;
    transition: all 0.3s;
  }

  .nav.open {
    transform: translateY(0);
    opacity: 1;
    pointer-events: auto;
  }

  .menu-toggle {
    display: flex;
  }

  .header-actions :deep(.insta-btn span) {
    display: none;
  }
}
</style>