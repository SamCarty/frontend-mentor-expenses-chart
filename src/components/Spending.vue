<script setup>
import { computed } from "vue";
import SpendingGraph from "./SpendingGraph.vue";
import SpendingTotal from "./SpendingTotal.vue";

const props = defineProps({
  spending: { type: Array, required: true },
});

const total = computed(() => {
  return props.spending.reduce((acc, item) => acc + item.amount, 0);
});
</script>

<template>
  <div class="spending-wrapper">
    <h1>Spending - Last 7 days</h1>
    <SpendingGraph :spending="spending" />
    <hr />
    <SpendingTotal :total="total" :change-percent="-2.4" />
  </div>
</template>

<style scoped>
.spending-wrapper {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 2rem;
  background-color: hsl(33, 100%, 98%);
  border-radius: 1.5rem;
  gap: 2rem;
}

.spending-wrapper h1 {
  color: hsl(25, 47%, 15%);
  font-size: 1.5rem;
  margin-bottom: 2rem;
}

.spending-wrapper hr {
  width: 100%;
  border: 1px solid hsl(25, 47%, 15%);
  opacity: 0.1;
}

@media screen and (min-width: 768px) {
  .spending-wrapper {
    padding: 2rem 3rem;
  }

  .spending-wrapper h1 {
    font-size: 2.25rem;
  }
}
</style>
