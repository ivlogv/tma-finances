<script setup lang="ts">
import { useRoute, useRouter } from 'vue-router'

// Ionicons 5
import {
  HomeOutline,
  GridOutline,
  AddCircleOutline,
  PieChartOutline,
  SettingsOutline
} from '@vicons/ionicons5'

const router = useRouter()
const route = useRoute()

const items = [
  { label: 'Home', icon: HomeOutline, path: '/' },
  { label: 'Categories', icon: GridOutline, path: '/categories' },
  { label: 'Add', icon: AddCircleOutline, path: '/add' },
  { label: 'Analytics', icon: PieChartOutline, path: '/analytics' },
  { label: 'Settings', icon: SettingsOutline, path: '/theme-params' }
]

function isActive(path: string) {
  return route.path === path
}

function navigate(path: string) {
  router.push(path)
}
</script>

<template>
  <nav class="bottom-nav">
    <div
      v-for="item in items"
      :key="item.path"
      class="nav-item"
      :class="{ active: isActive(item.path) }"
      @click="navigate(item.path)"
    >
      <n-icon :component="item.icon" size="22" />
      <span class="label">{{ item.label }}</span>
    </div>
  </nav>
</template>

<style scoped>
.bottom-nav {
  width: 100%;
  display: flex;
  justify-content: space-around;
  align-items: center;
  gap: 8px;
  
  background: var(--tg-theme-bg-color);
  z-index: 100;
}

.nav-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 4px;
  min-width: 48px;

  padding: 6px 0;
  cursor: pointer;

  font-size: 12px;
  color: var(--tg-theme-hint-color);

  transition: background 0.2s ease, color 0.2s ease;
  border-radius: 12px;
}

.nav-item.active {
  background: var(--tg-theme-button-color);
  color: var(--tg-theme-button-text-color);
}

.nav-item.active .label {
  color: var(--tg-theme-button-text-color);
}

.label {
  font-size: 11px;
}
</style>