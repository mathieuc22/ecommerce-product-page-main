<template>
  <div class="product">
    <div class="row">
      <div class="col gallery">
        
      </div>
      <div class="col summary">
        <div class="summary__brand">{{ product.brand }}</div>
        <h1 class="summary__name">{{ product.name }}</h1>
        <p class="summary__description">{{ product.description }}</p>
        <div class="price">
          <span class="price__current">{{ product.price.current }}</span>
          <div class="discount">50%</div>
          <span class="price__was">{{ product.price.was }}</span>
        </div>
        <div class="quantity">
          <span class="quantity__btn">-</span>
          <span class="quantity__value">0</span>
          <span class="quantity__btn">+</span>
        </div>
        <div class="cart">
          <button class="btn">Add to cart</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps(['product'])
</script>