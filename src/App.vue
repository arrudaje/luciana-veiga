<script setup lang="ts">
import { RouterView } from 'vue-router'
</script>

<template>
  <header class="app__header">
    <div class="app__header__logo">
      Luciana Veiga
    </div>
  </header>

  <RouterView />
</template>

<style scoped lang="scss">
.app {
  &__header {
    display: flex;
    flex-direction: column;
    position: relative;
    background: black;
    color: var(--color-background);
    padding: 2rem;
    background-image: url(./assets/header.jpg);
    background-size: 50%;
    background-repeat: no-repeat;
    background-position-y: 23%;
    background-position-x: 100%;
    background-blend-mode: hard-light;

    &__logo {
      font-size: 90px;
      margin: 90px;
      z-index: 1;
      font-weight: 700;
    }
  }
}
</style>
