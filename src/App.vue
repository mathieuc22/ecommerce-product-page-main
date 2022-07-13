<template>
  <AppHeader />
  <ProductPage :product="product" />
</template>

<script setup>
import ProductPage from './components/ProductPage.vue';
import AppHeader from './components/AppHeader.vue';

const product = {
  brand: "Sneaker Company",
  name: "Fall Limited Edition Sneakers",
  description: "These low-profile sneakers are your perfect casual wear companion. Featuring a durable rubber outer sole, they’ll withstand everything the weather can offer.",
  price: {
    current: "$125.00",
    was: "$250.00"
  },
  photos: [
    {
      id: 0,
      fullsize: "image-product-1.jpg",
      thumbnail: "image-product-1-thumbnail.jpg"
    },
    {
      id: 1,
      fullsize: "image-product-2.jpg",
      thumbnail: "image-product-2-thumbnail.jpg"
    },
    {
      id: 2,
      fullsize: "image-product-3.jpg",
      thumbnail: "image-product-3-thumbnail.jpg"
    },
    {
      id: 3,
      fullsize: "image-product-4.jpg",
      thumbnail: "image-product-4-thumbnail.jpg"
    }
  ]
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
