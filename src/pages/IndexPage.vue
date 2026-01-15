<script setup lang="ts">
// import { computed } from "vue";
// import { routes } from "@/router";
import AppPage from "@/components/AppPage.vue";
// import AppLink from "@/components/AppLink.vue";
import BottomNav from "@/components/BottomNav.vue";

import { WalletOutline } from "@vicons/ionicons5";

// const nonIndexRoutes = computed(() => routes.filter((r) => !!r.meta?.title));
</script>

<template>
  <AppPage title="Home Page" :back="false">
    <n-card :bordered="false">
      <div class="hstack balance-row">
        <n-icon :component="WalletOutline" size="22" />
        <span class="balance-label">Current Balance</span>
      </div>
      <h2>$12,345.67</h2>
      <span class="currency-tag">USD</span>
    </n-card>

    <h3>Recent Transactions</h3>

    <template #bottom>
      <BottomNav />
    </template>
  </AppPage>
</template>

<style scoped>
  h2 {
    margin-block: 0.2em;
  }
.hstack {
  display: flex;
  align-items: center; /* выравнивание по вертикали */
}

.balance-row {
  display: flex;
  align-items: center;
  gap: 8px;
}

.balance-label {
  font-size: 14px;
  font-weight: 500;
  margin-top: 2px;
  color: var(--tg-subtitle-hint-color);
}

.n-card {
  border-radius: 16px;
  background-color: var(--tg-theme-button-color);
  color: var(--tg-theme-button-text-color);
}

.index-page__links {
  list-style: none;
  padding-left: 0;
}

.index-page__link {
  font-weight: bold;
  display: inline-flex;
  gap: 5px;
}

.index-page__link-item + .index-page__link-item {
  margin-top: 10px;
}

.index-page__link-icon {
  width: 20px;
  display: block;
}

.index-page__link-icon svg {
  display: block;
}

.index-page__section {
  border-radius: 16px;
  margin-bottom: 20px;
}
</style>
