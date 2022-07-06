<template>

  <div class="gallery">
    <div @click="modal = true" class="gallery__image">
      <img :src="getImgUrl(photos[selected].fullsize)" alt="Product image">
    </div>
    <ul class="gallery__thumbnails">
      <li v-for="(photo, index) in photos" :key="index" class="gallery__thumbnail" @click="selected = index"
        :class="{ selected: selected === index }">
        <img :src="getImgUrl(photo.thumbnail)" alt="Product thumbnail">
      </li>
    </ul>
  </div>

  <ImageGalleryModal :modal="modal" :photos="photos" @close="modal = false" />

</template>

<script setup>
import ImageGalleryModal from './ImageGalleryModal.vue';
import { ref } from 'vue';
defineProps(['photos'])

const selected = ref(0)

const modal = ref(false)

function getImgUrl(url) {
  return new URL(url, import.meta.url).href
}

</script>

<style lang="scss">
.gallery {
  display: flex;
  flex-direction: column;
  padding: 20px;
  gap: 20px;
  height: 100%;
  width: auto;

  & img {
    display: block;
    height: 100%;
    object-fit: cover;
  }

  &__image {
    overflow: hidden;
    display: flex;
    justify-content: center;

    & img {
      object-fit: contain;
      border-radius: 10px;
    }
  }

  &__thumbnails {
    width: 100%;
    list-style: none;
    display: flex;
    justify-content: center;
    gap: 20px;
  }

  &__thumbnail {
    background-color: $color-neutral-White;
    border-radius: 10px;
    overflow: hidden;
    cursor: pointer;
    margin: 2px;
    max-height: 92px;
    max-width: 92px;
  }

}

.selected {
  border: 2px solid $color-primary-Orange;
  margin: 0px;

  & img {
    filter: opacity(0.3);
  }
}
</style>