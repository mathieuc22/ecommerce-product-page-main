<template>

  <div class="gallery">
    <div @click="lightbox = true" class="gallery__image">
      <img :src="getImgUrl(photos[selected].fullsize)" alt="Product image">
    </div>
    <ul class="gallery__thumbnails">
      <li v-for="(photo, index) in photos" :key="index" class="gallery__thumbnail" @click="selected = index"
        :class="{ selected: selected === index }">
        <img :src="getImgUrl(photo.thumbnail)" alt="Product thumbnail">
      </li>
    </ul>
  </div>

  <Lightbox v-if="lightbox" :photos="photos" @close="lightbox = false" />

</template>

<script setup>
import Lightbox from './Lightbox.vue';
import { ref } from 'vue';
defineProps(['photos'])

const selected = ref(0)

const lightbox = ref(false)

function getImgUrl(url) {
  return new URL(url, import.meta.url).href
}

</script>

<style lang="scss">
.gallery {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 20px;
  gap: 20px;
  height: 100%;
  width: auto;

  & img {
    display: block;
  }

  &__image {
    display: flex;
    justify-content: center;
    flex-direction: column;
    position: relative;
    height: 61vh;

    & img {
      display: block;
      height: 100%;
      width: 100%;
      object-fit: contain;
      border-radius: 10px;
    }
  }

  &__thumbnails {
    list-style: none;
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 445px;
  }

  &__thumbnail {
    background-color: $color-neutral-White;
    border-radius: 10px;
    overflow: hidden;
    cursor: pointer;
    max-height: 92px;
    max-width: 92px;
  }

}

.selected {
  border: 2px solid $color-primary-Orange;

  & img {
    filter: opacity(0.3);
  }
}
</style>