<template>

    <div v-if="modal" class="modal">
        <div class="gallery">
            <div class="gallery__image">
                <img :src="getImgUrl(photos[selected].fullsize)" alt="Product image">
                <button @click="selected > 0 ? selected-- : selected = photos.length - 1">Prev</button>
                <button @click="selected < photos.length - 1 ? selected++ : selected = 0">Next</button>
                <button @click="$emit('close')">Close</button>
            </div>
            <ul class="gallery__thumbnails">
                <li v-for="(photo, index) in photos" :key="index" class="gallery__thumbnail" @click="selected = index"
                    :class="{ selected: selected === index }">
                    <img :src="getImgUrl(photo.thumbnail)" alt="Product thumbnail">
                </li>
            </ul>
        </div>
    </div>

</template>

<script setup>
import { ref } from 'vue';
defineProps(['photos', 'modal'])

const selected = ref(0)

function getImgUrl(url) {
    return new URL(url, import.meta.url).href
}
</script>

<style lang="scss" scoped>
.modal {
    background-color: rgba(0, 0, 0, 0.75);
    position: fixed;
    z-index: 999;
    top: 0;
    left: 0;
    height: 100%;
    width: 100%;
    display: flex;
    align-content: center;
    justify-content: center;
    resize: horizontal;
}
</style>
