<script setup>
defineProps({
  balance: { type: Number, required: true },
});
</script>

<template>
  <div class="balance-wrapper">
    <div class="balance">
      <h2>My balance</h2>
      <span>${{ balance.toLocaleString() }}</span>
    </div>
    <div class="logo">
      <img src="../assets/logo.svg" alt="Logo" />
    </div>
  </div>
</template>

<style scoped>
.balance-wrapper {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 2rem;
  background-color: hsl(10, 79%, 65%);
  border-radius: 1.5rem;
}

.balance {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  gap: 0.5rem;
  color: hsl(27, 66%, 92%);
}

.balance h2 {
  font-size: 1rem;
  font-weight: 400;
}

.balance span {
  font-size: 2rem;
  font-weight: 700;
  color: hsl(33, 100%, 98%);
}

@media screen and (min-width: 768px) {
  .balance {
    gap: 1rem;
  }

  .balance h2 {
    font-size: 1.25rem;
  }

  .balance span {
    font-size: 2.25rem;
  }
}

.logo img {
  width: 5rem;
  height: 5rem;
}
</style>
