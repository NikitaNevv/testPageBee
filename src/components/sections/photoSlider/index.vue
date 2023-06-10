<template>
        <swiper
            class="photo-slider"
            :modules="modules"
            :slides-per-view="1"
            :space-between="20"
        >
            <swiper-slide
                class="photo-slider__box"
                v-for="image in images"
                :key="image.id"
            >
                <div
                    class="photo-slider__back"
                    :style="{'background-image': 'url(' + image.img + ')'}"
                ></div>

                <img class="photo-slider__image" :src="image.img" alt="car image">
            </swiper-slide>

            <IconsSliderIcon class="photo-slider__btn"/>

            <div class="photo-slider__counter">
                {{countImages}}
            </div>
        </swiper>
</template>

<script>
export default {name: 'SectionsPhotoSlider'}
</script>

<script setup>
import {Navigation, Pagination, Scrollbar, A11y} from 'swiper'

// Import Swiper Vue.js components
import {Swiper, SwiperSlide} from 'swiper/vue'

// Import Swiper styles
import 'swiper/css'
import 'swiper/css/pagination'
import {computed, reactive} from 'vue'
import IconsSliderIcon from '../../icons/sliderIcon/index.vue'

const images = reactive([
    {
        img: './src/assets/images/forSlider/big-size-image.png',
        id: '1'
    },
    {
        img: './src/assets/images/forSlider/big-size-image.png',
        id: '2'
    },
    {
        img: './src/assets/images/forSlider/small-size-image.png',
        id: '3'
    },
],
)

const countImages = computed(() => {
    return images.length;
})

const currentPhotoNum = computed(() => {

})

</script>

<style lang="scss" scoped>
.photo-slider {
    &__box {
        position: relative;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    &__back {
        position: absolute;
        width: 100%;
        height: 100%;
        background-repeat: no-repeat;
        background-size: cover;
        background-position: center;
        filter: brightness(30%);
    }

    &__image {
        position: relative;
        max-width: 778px;
        max-height: 484px;
    }

    &__btn {
        position: absolute;
        z-index: 1;
        top: 36px;
        right: 36px;
        cursor: pointer;
    }

    &__counter {
        position: absolute;
        z-index: 1;
        bottom: 14px;
        left: 50%;
        transform: translateX(-50%);
        display: flex;
        align-items: center;
        justify-content: center;
        min-width: 53px;
        height: 22px;
        background-color: rgba(0, 0, 0, 0.5);
        border-radius: 19px;
        font-family: $mulish-font;
        color: $color-snow;
        font-style: normal;
        font-weight: 600;
        font-size: 12px;
        line-height: 1;
    }
}
</style>
