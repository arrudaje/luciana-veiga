<script setup lang="ts">
import Product from "../components/Product.vue"
</script>

<template>
  <main class="home">
    <Product image="bolo" name="Bolo" :price="400" :variants="['chocolate', 'baunilha']" />
  </main>
</template>

<style lang="scss" scoped>
.home {
  margin: 0 90px 90px;
  padding: 0 2rem;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  grid-column-gap: 1rem;
}
</style>