<script setup lang="ts">
// import { computed } from "vue";
// import { routes } from "@/router";
import AppPage from "@/components/AppPage.vue";
// import AppLink from "@/components/AppLink.vue";
import BottomNav from "@/components/BottomNav.vue";
import TransactionCard from "@/components/TransactionCard.vue";

import { WalletOutline, HomeOutline, RestaurantOutline } from "@vicons/ionicons5";

// const nonIndexRoutes = computed(() => routes.filter((r) => !!r.meta?.title));
const data = {
  balance: 12345.67,
  currency: "USD",
  transactions: [
    {
      date: "2022-01-01",
      title: "Groceries",
      amount: 500,
      description: "Groceries at Dionis",
      category: "Groceries",
      icon: RestaurantOutline,
    },
    {
      date: "2022-02-01",
      title: "Rent",
      amount: -1000,
      description: "Rent for august",
      category: "Housing",
      icon: HomeOutline,
    },
  ],
};
</script>

<template>
  <AppPage title="Home Page" :back="false">

    <n-card :bordered="false" class="balance-card">
      <n-flex vertical gap="6">
        <!-- Заголовок -->
        <n-flex align="center" gap="8">
          <n-icon size="18" class="icon" :component="WalletOutline" />
          <n-text depth="2" class="title"> Current Balance </n-text>
        </n-flex>

        <!-- Сумма -->
        <n-text class="amount"> ${{ data.balance.toFixed(2) }} </n-text>

        <!-- Валюта -->
        <n-text depth="3" class="currency">
          {{ data.currency ?? "USD" }}
        </n-text>
      </n-flex>
    </n-card>

    <h3>Recent Transactions</h3>

    <n-flex vertical>
      <div v-for="tx in data.transactions" :key="tx.date">
        <TransactionCard
          :title="tx.title"
          :subtitle="tx.description"
          :amount="tx.amount"
          :date="tx.date"
          :icon="tx.icon"
        />
      </div>
    </n-flex>

    <template #bottom>
      <BottomNav />
    </template>
  </AppPage>
</template>

<style scoped>
.balance-card {
  background: var(--tg-theme-button-color);
  color: var(--tg-theme-text-color);
  border-radius: 16px;
}

.title {
  color: var(--tg-theme-text-color);
}

.amount {
  font-size: 26px;
  font-weight: 700;
  line-height: 1.1;
  color: var(--tg-theme-text-color);
}

.currency {
  font-size: 12px;
  color: rgba(255, 255, 255, 0.7);
}

.icon {
  color: var(--tg-theme-text-color);
}
</style>
