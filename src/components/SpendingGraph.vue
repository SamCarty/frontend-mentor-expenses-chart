<script setup>
import { defineProps, computed } from "vue";
import SpendingItem from "./SpendingItem.vue";

const props = defineProps({
  spending: { type: Array, required: true },
});

const normalisedSpending = computed(() => {
  const max = Math.max(...props.spending.map((item) => item.amount));
  const min = Math.min(...props.spending.map((item) => item.amount));
  return props.spending.map((item) => ({
    ...item,
    height: ((item.amount - min) / (max - min)) * 100 + 50,
  }));
});

const currentDayIndex = computed(() => {
  return new Date().getDay() - 1;
});
</script>

<template>
  <div class="spending-graph">
    <SpendingItem
      v-for="(spend, index) in normalisedSpending"
      :key="spend.day"
      :amount="spend.amount"
      :height="spend.height"
      :label="spend.day"
      :highlighted="index === currentDayIndex"
    />
  </div>
</template>

<style scoped>
.spending-graph {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
}
</style>
