<script lang="ts" setup>
import cupcake from '../assets/header.jpg'
</script>

<template>
  <svg xmlns="http://www.w3.org/2000/svg" viewBox="-30 -30 295 295" class="hero-image" font-size="9" font-family="'Grandstander', sans-serif">
    <defs>
      <path
        id="shape"
        d="M57.26,12.16c-20.65,6.23-36.85,5.75-50.36,70.07C-6.61,146.56-9.07,241.13,84.28,232.54c93.35-8.6,126.47-24.54,143.67-49.1,17.2-24.56,3.55-49.35,6.78-67.61,7.18-40.64-15.25-152.63-177.47-103.66Z"
      />
      <clipPath id="clippath">
        <use href="#shape" />
      </clipPath>
    </defs>
    <image :href="cupcake" width="120%" x="-20%" y="-5%" clip-path="url(#clippath)"></image>
    <text dy="20" transform="translate(15,0) rotate(5)">
      <textPath href="#shape">
        <animate attributeName="startOffset" values="350;345;350" dur="5s" repeatCount="indefinite" />
        1. Building trust 2. The best moments are together 3. Incredulous smiling 4. Homemade flavors 5. Classic ingredients 6. This tastes like home
      </textPath>
    </text>
    <text dy="22" transform="translate(0,-3)">
      <textPath href="#shape">
        <animate attributeName="startOffset" values="0;5;0" dur="5s" repeatCount="indefinite"  />
        7. Be free and not pretentious 8. La bonne vivre 9. Best source, honest delivery 10. Homemade flavors 11. Classic ingredients 12. This tastes like home
      </textPath>
    </text>
  </svg>
</template>

<style lang="scss" scoped>
.hero-image {
  text-transform: uppercase;
}
</style>
