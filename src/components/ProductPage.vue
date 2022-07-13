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
            <button class="button">
              <svg width="22" height="20" xmlns="http://www.w3.org/2000/svg"><path d="M20.925 3.641H3.863L3.61.816A.896.896 0 0 0 2.717 0H.897a.896.896 0 1 0 0 1.792h1l1.031 11.483c.073.828.52 1.726 1.291 2.336C2.83 17.385 4.099 20 6.359 20c1.875 0 3.197-1.87 2.554-3.642h4.905c-.642 1.77.677 3.642 2.555 3.642a2.72 2.72 0 0 0 2.717-2.717 2.72 2.72 0 0 0-2.717-2.717H6.365c-.681 0-1.274-.41-1.53-1.009l14.321-.842a.896.896 0 0 0 .817-.677l1.821-7.283a.897.897 0 0 0-.87-1.114ZM6.358 18.208a.926.926 0 0 1 0-1.85.926.926 0 0 1 0 1.85Zm10.015 0a.926.926 0 0 1 0-1.85.926.926 0 0 1 0 1.85Zm2.021-7.243-13.8.81-.57-6.341h15.753l-1.383 5.53Z" fill="#69707D" fill-rule="nonzero"/></svg>
              Add to cart
              </button>
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

  & svg path {
    fill: $color-neutral-White;
  }

  &:hover {
    background-color: lighten($color: $color-primary-Orange, $amount: 20);
  }

  &:active {
    transform: translateY(2px);
  }
}
</style>