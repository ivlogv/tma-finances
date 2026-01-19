<script setup lang="ts">
import { NCard, NFlex, NIcon, NText } from "naive-ui";
import type { Component } from 'vue'

defineProps<{
  title: string;
  subtitle?: string;
  amount: number;
  date: string;
  icon: Component;
}>();
</script>

<template>
  <n-card size="small" :bordered="false" class="transaction-card">
    <n-flex align="center">
      <!-- Левая группа: иконка + текст -->
      <n-flex align="center" gap="8">
        <div class="icon">
          <n-icon size="22" :component="icon"/>
        </div>

        <n-flex vertical size="small">
          <n-text strong class="transaction-card__title">{{ title }}</n-text>
          <n-text depth="3" style="font-size: 12px">
            {{ subtitle }}
          </n-text>
        </n-flex>
      </n-flex>

      <!-- Spacer -->
      <div class="spacer" />

      <!-- Правая часть -->
      <n-flex vertical align="end" size="small">
        <n-text :type="amount < 0 ? 'error' : 'success'">
          {{ amount < 0 ? "-" : "+" }}${{ Math.abs(amount).toFixed(2) }}
        </n-text>
        <n-text depth="3" style="font-size: 12px">
          {{ date }}
        </n-text>
      </n-flex>
    </n-flex>
  </n-card>
</template>

<style scoped>
.transaction-card {
  border-radius: 16px;
}

.transaction-card__title {
  color: var(--tg-theme-text-color);
}

.icon {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background: var(--tg-theme-button-color);
  color: var(--tg-theme-text-color);
  display: flex;
  align-items: center;
  justify-content: center;
}

/* Ключевой момент */
.spacer {
  flex: 1;
}
</style>
