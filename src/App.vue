<template>
  <AppHeader />
  <ProductPage :product="product" />
</template>

<script setup>
import ProductPage from './components/ProductPage.vue';
import AppHeader from './components/AppHeader.vue';
import { computed } from 'vue';
import { useStore } from 'vuex';

const store = useStore()

const product = computed(() => store.getters['products/getProductById'](0))

store.dispatch('products/getAllProducts')

</script>

<style lang="scss">
#app {
  font-family: $font-family-default;
  font-size: $font-size-default;
  font-weight: $font-weight-default;
  position: relative;
}
</style>
