<script setup>
import { defineProps } from "vue";

const props = defineProps({
  height: { type: Number, required: true },
  amount: { type: Number, required: true },
  label: { type: String, required: true },
  highlighted: { type: Boolean, default: false },
});
</script>

<template>
  <div class="spending-item">
    <div
      class="spending-bar"
      :style="{ height: height + 'px' }"
      :class="{ highlighted }"
    ></div>
    <span class="spending-label">{{ label }}</span>

    <div class="spending-amount">
      <span>${{ amount.toLocaleString() }}</span>
    </div>
  </div>
</template>

<style scoped>
.spending-item {
  display: flex;
  flex-direction: column;
  position: relative;
  gap: 0.5rem;
  width: 12%;
}

.spending-bar {
  background-color: hsl(10, 79%, 65%);
  width: 100%;
  border-radius: 0.4rem;
  transition: opacity 0.2s ease-in-out;
  cursor: pointer;
}

.spending-bar.highlighted {
  background-color: hsl(186, 34%, 60%);
}

.spending-bar:hover {
  opacity: 0.7;
}

.spending-label {
  display: block;
  text-align: center;
  color: hsl(28, 10%, 53%);
}

.spending-amount {
  display: none;
  justify-content: center;
  align-items: center;
  position: absolute;
  background-color: hsl(25, 47%, 15%);
  padding: 0.5rem;
  border-radius: 0.25rem;
  color: hsl(33, 100%, 98%);
  top: -2.5rem;
  left: 50%;
  transform: translateX(-50%);
  z-index: 1;
}

.spending-amount span {
  font-size: 1rem;
  font-weight: 700;
}

.spending-bar:hover ~ .spending-amount {
  display: flex;
}
</style>
