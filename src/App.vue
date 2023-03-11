<script setup>
import MyBalance from "./components/MyBalance.vue";
import Spending from "./components/Spending.vue";
import spending from "./assets/data.json";
</script>

<template>
  <main class="app">
    <MyBalance :balance="921.48" />
    <Spending :spending="spending" />
  </main>
</template>

<style scoped>
.app {
  display: flex;
  flex-direction: column;
  justify-content: center;
  max-width: 500px;
  margin: 0 auto;
  min-height: 100vh;
  gap: 2rem;
  padding: 0 1rem;
}

@media screen and (min-width: 768px) {
  .app {
    padding: 0 1rem;
  }
}
</style>

<style>
body {
  font-family: "DM Sans", sans-serif;
  background-color: hsl(27, 66%, 92%);
}
</style>
