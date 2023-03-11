<script setup>
import { computed } from "vue";

const props = defineProps({
  total: { type: Number, required: true },
  changePercent: { type: Number, required: true },
});

const sign = computed(() => {
  return props.changePercent > 0 ? "+" : "";
});
</script>

<template>
  <div class="spending-total-wrapper">
    <div class="spending-total">
      <h2>Total this month</h2>
      <span>${{ total.toLocaleString() }}</span>
    </div>
    <div class="spending-change">
      <span class="change-percent"
        >{{ sign }}{{ changePercent.toLocaleString() }}%</span
      >
      <span class="change-percent-period">from last month</span>
    </div>
  </div>
</template>

<style scoped>
.spending-total-wrapper {
  display: flex;
  justify-content: space-between;
  flex-direction: column;
  gap: 1.5rem;
}

@media screen and (min-width: 375px) {
  .spending-total-wrapper {
    flex-direction: row;
    gap: 1rem;
  }
}

.spending-total {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  gap: 0.5rem;
  color: hsl(28, 10%, 53%);
}

.spending-total h2 {
  font-size: 1rem;
  font-weight: 400;
}

.spending-total span {
  font-size: 2rem;
  font-weight: 700;
  color: hsl(25, 47%, 15%);
}

.spending-change {
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  align-items: flex-start;
  color: hsl(28, 10%, 53%);
}

@media screen and (min-width: 375px) {
  .spending-change {
    align-items: flex-end;
  }
}

.change-percent {
  font-size: 1.25rem;
  font-weight: 700;
  color: hsl(25, 47%, 15%);
}
</style>
