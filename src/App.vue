<template>
    <div class="page-main">
        <SectionHeader class="page-main__header"/>

        <SectionsPhotoSlider/>

        <div class="wrapper page-main__offer">
            <SectionClientOptions/>

            <SectionsUserOffer/>
        </div>
    </div>
</template>

<script setup>
import SectionHeader from './components/sections/header/index.vue'
import SectionsPhotoSlider from './components/sections/photoSlider/index.vue'
import SectionClientOptions from './components/sections/clientDescription/index.vue'
import SectionsUserOffer from './components/sections/userOffer/index.vue'
</script>

<style lang="scss" scoped>
.page-main {
    &__offer {
        display: flex;
        gap: 70px;
        margin-top: 42px;

        padding-bottom: 100px;
    }
}
</style>
