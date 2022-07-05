<template>
  <div class="product">
    <div class="row">
      <div class="col gallery">
        <ImageGallery :photos="product.photos" />
      </div>
      <div class="col summary">
        <div class="summary__brand">{{ product.brand }}</div>
        <h1 class="summary__name">{{ product.name }}</h1>
        <p class="summary__description">{{ product.description }}</p>
        <div class="price">
          <div class="price__current">{{ product.price.current }}
            <span class="discount">50%</span>
          </div>
          <div class="price__was">{{ product.price.was }}</div>
        </div>
        <div class="row">
          <div class="quantity">
            <span @click="decrement" class="quantity__btn"><img src="../assets/images/icon-minus.svg" alt="icon minus"></span>
            <span class="quantity__value">{{ count }}</span>
            <span @click="increment" class="quantity__btn"><img src="../assets/images/icon-plus.svg" alt="icon plus"></span>
          </div>
          <div class="cart">
            <button class="button"><img src="../assets/images/icon-cart.svg" alt="icon cart"> Add to cart</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import ImageGallery from './ImageGallery.vue';

defineProps(['product'])

// reactive state
const count = ref(0)

// functions that mutate state and trigger updates
function increment() {
  if (count.value < 10) {count.value++}
}
// functions that mutate state and trigger updates
function decrement() {
  if (count.value > 0) {count.value--}
}

</script>

<style lang="scss" scoped>
.summary {
  &__brand {
    color: $color-primary-Orange;
    font-weight: 700;
    font-size: 0.8em;
    letter-spacing: 2px;
    text-transform: uppercase;
  }

  &__name {
    font-size: 2.7em;
    font-weight: 700;
  }

  &__description {
    color: $color-neutral-Dark-grayish-blue;
  }
}

.price {
  &__current {
    font-size: 1.6em;
    font-weight: 700;
  }

  &__was {
    font-size: 1.1em;
    font-weight: 700;
    text-decoration: line-through;
    color: $color-neutral-Grayish-blue;
  }
}

.discount {
  display: inline-block;
  text-decoration: none;
  font-size: 15px;
  font-weight: 700;
  background-color: $color-primary-Pale-orange;
  color: $color-primary-Orange;
  border: none;
  border-radius: 5px;
  padding: 5px 9px;
  user-select: none;
}

.quantity {
  width: 35%;
  height: 56px;
  font-size: 1em;
  font-weight: 700;
  background-color: $color-neutral-Light-grayish-blue;
  color: $color-neutral-Black;
  border-radius: 10px;
  display: flex;
  align-items: center;
  user-select: none;
  
  & > * {
    flex: 1;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  &__btn {
    cursor: pointer;
  }
}

.cart {
  width: 65%;
}

.button {
  width: 100%;
  height: 56px;
  cursor: pointer;
  text-decoration: none;
  font-size: 1em;
  font-weight: 700;
  background-color: $color-primary-Orange;
  color: $color-neutral-White;
  border: none;
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 9px 39px;
  transition: all 0.2s ease-in-out;

  &:hover {
    background-color: lighten($color: $color-primary-Orange, $amount: 20);
  }

  &:active {
    transform: translateY(2px);
  }
}
</style>