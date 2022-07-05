<template>
  <ProductPage :product="product" />
</template>

<script setup>
import ProductPage from './components/ProductPage.vue';

const product = {
  brand: "Sneaker Company",
  name: "Fall Limited Edition Sneakers",
  description: "These low-profile sneakers are your perfect casual wear companion. Featuring a durable rubber outer sole, they’ll withstand everything the weather can offer.",
  price: {
    current: "$125.00",
    was: "$250.00"
  }
}

</script>

<style lang="scss">
#app {
  font-family: $font-family-default;
  font-size: $font-size-default;
  font-weight: $font-weight-default;
  position: relative;
}
</style>
