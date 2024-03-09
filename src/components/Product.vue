<script lang="ts" setup>
import { onMounted, ref } from 'vue'

const props = defineProps<{
  image: string
  name: string
  price: number
  variantName?: string
  variants?: Array<string>
}>()

const emit = defineEmits(['addedToCart'])

const amount = ref(0)
const variant = ref(null)
</script>

<template>
  <div class="product">
    <div class="product__image">
      <img :src="image" :alt="name" class="product__image__img" />
    </div>
    <div class="product__main">
      <div class="product__main__name">{{ name }}</div>
      <div class="product__main__price">{{ price }}</div>
    </div>
    <div v-if="variants" class="product__variant">
      <label for="variant-select" class="product__variant__label"
        >{{ variantName ?? 'Opção' }}:</label
      >
      <select v-model="variant" class="product__variant__select">
        <option :value="null" disabled selected>Selecione...</option>
        <option v-for="v in variants" :key="v" value="v">{{ v }}</option>
      </select>
    </div>
    <div class="product__add-to-cart">
      <div class="product__add-to-cart__amount">
        <button
          class="product__add-to-cart__amount__button"
          :class="{ 'product__add-to-cart__amount__button--disabled': amount === 0 }"
          @click="amount--"
        >
          -
        </button>
        {{ amount }}
        <button class="product__add-to-cart__amount__button" @click="amount++">+</button>
      </div>
      <button
        class="product__add-to-cart__button"
        :class="{ 'product__add-to-cart__button--disabled': !variant || !amount }"
      >
        Adicionar
        <svg
          xmlns="http://www.w3.org/2000/svg"
          viewBox="0 0 576 512"
          class="product__add-to-cart__button__icon"
        >
          <path
            d="M0 24C0 10.7 10.7 0 24 0H69.5c22 0 41.5 12.8 50.6 32h411c26.3 0 45.5 25 38.6 50.4l-41 152.3c-8.5 31.4-37 53.3-69.5 53.3H170.7l5.4 28.5c2.2 11.3 12.1 19.5 23.6 19.5H488c13.3 0 24 10.7 24 24s-10.7 24-24 24H199.7c-34.6 0-64.3-24.6-70.7-58.5L77.4 54.5c-.7-3.8-4-6.5-7.9-6.5H24C10.7 48 0 37.3 0 24zM128 464a48 48 0 1 1 96 0 48 48 0 1 1 -96 0zm336-48a48 48 0 1 1 0 96 48 48 0 1 1 0-96z"
          />
        </svg>
      </button>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.product {
  position: relative;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;

  &__image {
    border-radius: 16px;
    overflow: hidden;
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 0;
    padding-bottom: 100%;
    background: var(--color-text);

    &__img {
      position: absolute;
      width: auto;
      height: auto;
      left: 0;
      right: 0;
      top: 0;
      bottom: 0;
      max-width: 100%;
      max-height: 100%;
      margin: auto;
    }
  }

  &__main {
    display: flex;
    justify-content: space-between;
    font-weight: 700;
    font-size: 24px;

    &__price {
      &::before {
        content: 'R$';
        margin-right: 0.25em;
      }
    }
  }

  &__variant {
    display: flex;
    justify-content: space-between;

    &__select {
      font-family: 'Figtree';
      background: none;
      border: none;
      font-size: 16px;
      color: var(--color-secondary);
    }
  }

  &__add-to-cart {
    display: flex;
    gap: 1rem;
    align-items: center;

    &__amount {
        font-size: 24px;
        display: flex;
        justify-content: space-between;
        width: 75px;

        &__button {
            cursor: pointer;
            font-size: 24px;
            background: none;
            border: none;
            font-weight: 700;

            &--disabled {
                pointer-events: none;
            }
        }
    }

    &__button {
      flex: 1;
      padding: 1rem;
      background: var(--color-secondary);
      color: var(--color-background);
      border: none;
      border-radius: 8px;
      font-size: 1rem;
      font-weight: 700;
      position: relative;
      cursor: pointer;

      &__icon {
        position: absolute;
        height: 1.2rem;
        fill: var(--color-background);
        right: 1rem;
      }

      &--disabled {
        cursor: default;
        pointer-events: none;

        &::after {
          content: '';
          position: absolute;
          left: 0;
          top: 0;
          height: 100%;
          width: 100%;
          border-radius: 8px;
          background: rgba(white, 0.3);
        }
      }
    }
  }
}
</style>
