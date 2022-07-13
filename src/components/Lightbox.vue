<template>

    <div v-if="modal" class="modal">
        <div class="gallery">
            <div class="gallery__image">
                <button class="button button--close" @click="$emit('close')">
                    <img src="src/assets/images/icon-close.svg" alt="icon close">
                </button>
                <img :src="getImgUrl(photos[selected].fullsize)" alt="Product image">
                <button class="button button--round button--prev"
                    @click="selected > 0 ? selected-- : selected = photos.length - 1">
                    <img src="src/assets/images/icon-previous.svg" alt="icon previous">
                </button>
                <button class="button button--round button--next"
                    @click="selected < photos.length - 1 ? selected++ : selected = 0">
                    <img src="src/assets/images/icon-next.svg" alt="icon next">
                </button>
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
    padding-top: 27px;
}

.button {
    position: absolute;
    cursor: pointer;
    border: none;
    background: none;
    display: flex;

    &--close {
        height: 24px;
        width: 24px;
        top: -46px;
        right: 0;
    }

    &--round {
        &::before {
            content: '';
            display: inline-block;
            background-color: $color-neutral-White;
            border-radius: 50%;
            height: 56px;
            width: 56px;
            position: absolute;
            z-index: -1;
        }

        border-radius: 50%;
        align-items: center;
        justify-content: center;
    }

    &--prev {
        left: 0;
        transform: translateX(-50%);
    }

    &--next {
        right: 0;
        transform: translateX(50%);
    }
}
</style>
