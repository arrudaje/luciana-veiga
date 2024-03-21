<script setup lang="ts">
import { RouterView } from 'vue-router'
import logo from './assets/logo.svg'
import HeroImage from './components/HeroImage.vue'
</script>

<template>
  <header class="app__header">
    <a href="/" class="app__header__logo">
      Luciana Veiga
      <span class="app__header__logo__subtitle">Bolos & Doces Artísticos</span>
      <img :src="logo" alt="Logotipo" class="app__header__logo__image" />
    </a>
    <div class="app__header__hero">
      <div class="app__header__hero__copy">make your week sweet!</div>
      <div class="app__header__hero__image">
        <HeroImage class="app__header__hero__image__main" />
      </div>
    </div>
  </header>

  <RouterView />
</template>

<style scoped lang="scss">
.app {
  &__header {
    display: flex;
    position: relative;
    color: var(--color-background);
    min-height: 500px;
    padding-left: calc(60px + 2rem);
    // background-image: url(./assets/header.jpg);
    // background-size: 50%;
    // background-repeat: no-repeat;
    // background-position-y: 23%;
    // background-position-x: 100%;
    // background-blend-mode: hard-light;

    &__logo {
      display: flex;
      align-items: baseline;
      position: absolute;
      width: 500px;
      left: 0;
      padding: 1rem;
      gap: 32px;
      font-size: 40px;
      font-weight: 700;
      font-family: 'fleur-display', sans-serif;
      color: var(--color-secondary);
      transform: rotate(270deg) translate(-205px, -205px);
      text-decoration: none;

      &__subtitle {
        font-family: 'Figtree', sans-serif;
        font-size: 12px;
      }

      &__image {
        width: 60px;
        margin-left: auto;
        align-self: flex-start;
      }
    }

    &__hero {
      display: flex;
      align-items: flex-end;
      gap: 32px;
      color: white;
      font-size: 160px;
      line-height: 100px;
      font-weight: 700;
      font-family: 'fleur', sans-serif;
      padding: 40px;

      &__image {
        flex: 1 0 auto;
        align-self: center;
        width: 400px;

        &__main {
          aspect-ratio: 1/1;
        }
      }
    }
  }

  @media screen and (max-width: 576px) {
    &__header {
      min-height: 100vh;
      padding-left: calc(60px + 1rem);

      &__logo {
        padding: 0.5rem;
        font-size: 50px;
        transform: rotate(270deg) translate(-187px, -187px);
        gap: 16px;
        width: 450px;
      }

      &__hero {
        padding: 16px;
        flex-direction: column;

        &__image {
          width: 100vw;
          position: absolute;
          bottom: 0;
          left: 0;
        }
      }
    }
  }
}
</style>
