<script setup>
defineProps({
  size: {
    type: String,
    default: 'normal', // normal | small
  },
})

const instagramUrl = 'https://instagram.com/kndev93'
</script>

<template>
  <a
    :href="instagramUrl"
    target="_blank"
    rel="noopener noreferrer"
    :class="['insta-btn', `size-${size}`]"
    title="ما را در اینستاگرام دنبال کنید"
  >
    <svg
      xmlns="http://www.w3.org/2000/svg"
      viewBox="0 0 24 24"
      fill="none"
      stroke="currentColor"
      stroke-width="2"
      stroke-linecap="round"
      stroke-linejoin="round"
      class="insta-icon"
    >
      <rect x="2" y="2" width="20" height="20" rx="5" ry="5"></rect>
      <path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"></path>
      <line x1="17.5" y1="6.5" x2="17.51" y2="6.5"></line>
    </svg>
    <span>@kndev93</span>
  </a>
</template>

<style scoped>
.insta-btn {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 12px 22px;
  border-radius: 10px;
  background: linear-gradient(45deg, #f09433, #e6683c, #dc2743, #cc2366, #bc1888);
  color: #fff;
  font-weight: 700;
  text-decoration: none;
  font-size: 0.95rem;
  transition: transform 0.2s, box-shadow 0.2s;
  white-space: nowrap;
}

.insta-btn.size-small {
  padding: 8px 16px;
  font-size: 0.85rem;
}

.insta-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 20px rgba(220, 39, 67, 0.35);
}

.insta-icon {
  width: 20px;
  height: 20px;
}

.size-small .insta-icon {
  width: 16px;
  height: 16px;
}
</style>