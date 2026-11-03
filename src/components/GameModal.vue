<script setup>
defineProps({
  project: {
    type: Object,
    required: true,
  },
})

defineEmits(['close'])
</script>

<template>
  <div class="modal-overlay" @click.self="$emit('close')">
    <div class="modal-box">
      <div class="modal-header">
        <h2>{{ project.emoji }} {{ project.title }}</h2>
        <button class="close-btn" @click="$emit('close')">✕</button>
      </div>

      <div class="modal-body">
        <iframe
          v-if="project.embedUrl"
          :src="project.embedUrl"
          class="game-frame"
          allowfullscreen
          frameborder="0"
        ></iframe>
        <div v-else class="no-embed">
          <p>این پروژه قابل نمایش مستقیم نیست.</p>
          <a :href="project.link" target="_blank" rel="noopener" class="btn-primary">
            باز کردن در تب جدید ↗
          </a>
        </div>
      </div>

      <div class="modal-footer">
        <p>{{ project.desc }}</p>
        <a :href="project.link" target="_blank" rel="noopener" class="btn-primary">
          مشاهده کامل ↗
        </a>
      </div>
    </div>
  </div>
</template>

<style scoped>
.modal-overlay {
  position: fixed;
  inset: 0;
  background: rgba(0, 0, 0, 0.8);
  backdrop-filter: blur(8px);
  display: grid;
  place-items: center;
  z-index: 100;
  padding: 24px;
  animation: fadeIn 0.2s ease;
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

.modal-box {
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: 20px;
  width: 100%;
  max-width: 1000px;
  max-height: 90vh;
  display: flex;
  flex-direction: column;
  overflow: hidden;
  animation: popUp 0.3s ease;
}

@keyframes popUp {
  from { transform: scale(0.95); opacity: 0; }
  to { transform: scale(1); opacity: 1; }
}

.modal-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 24px;
  border-bottom: 1px solid var(--border);
}

.modal-header h2 {
  font-size: 1.3rem;
  font-weight: 700;
}

.close-btn {
  background: var(--bg-soft);
  border: 1px solid var(--border);
  color: var(--text);
  width: 36px;
  height: 36px;
  border-radius: 10px;
  cursor: pointer;
  font-size: 1rem;
  transition: all 0.2s;
}

.close-btn:hover {
  border-color: var(--accent);
  color: var(--accent);
}

.modal-body {
  flex: 1;
  overflow: hidden;
  background: var(--bg);
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 400px;
}

.game-frame {
  width: 100%;
  height: 70vh;
  border: none;
}

.no-embed {
  text-align: center;
  padding: 40px;
  display: flex;
  flex-direction: column;
  gap: 16px;
  align-items: center;
}

.modal-footer {
  padding: 20px 24px;
  border-top: 1px solid var(--border);
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 16px;
  flex-wrap: wrap;
}

.modal-footer p {
  color: var(--text-muted);
  font-size: 0.9rem;
  flex: 1;
  min-width: 200px;
}
</style>