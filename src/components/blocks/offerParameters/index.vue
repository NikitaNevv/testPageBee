<template>
    <div class="blocks-offer-parameters">
        <div
            class="blocks-offer-parameters__box"
            v-for="param in parameters"
            :key="param.id"
        >
            <img :src="param.image" alt="parameter icon">
            <div class="blocks-offer-parameters__wrapper">
                <p class="blocks-offer-parameters__text">{{ param.text }}</p>
                <p class="blocks-offer-parameters__comment">{{ param.comment }}</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {name: 'BlocksOfferParameters'}
</script>

<script setup>
import {reactive} from 'vue'

const parameters = reactive([
    {
        image: './src/assets/images/forParameters/Mobile-Mechanic.svg',
        text: 'Mobile Mechanic Preferable',
        comment: '',
        id: 1,
    },
    {
        image: './src/assets/images/forParameters/Urgent.svg',
        text: 'Urgent',
        comment: '',
        id: 2,
    },
    {
        image: './src/assets/images/forParameters/Not-Drivable.svg',
        text: 'Not drivable ',
        comment: '',
        id: 3,
    },
    {
        image: './src/assets/images/forParameters/Own-parts.svg',
        text: 'Set of brand new 3 tier Michelin tires',
        comment: 'Own Parts',
        id: 4,
    }
])

</script>

<style lang="scss" scoped>
.blocks-offer-parameters {
    display: flex;
    flex-direction: column;
    gap: 40px;

    &__box {
        display: flex;
        align-items: center;
        gap: 10px;
    }

    &__wrapper {
        display: flex;
        flex-direction: column;
    }

    &__text {
        font-weight: 500;
        font-size: 15px;
        line-height: 1;
        color: $color-secondary-dark;
    }

    &__comment {
        font-family: $mulish-font;
        font-weight: 600;
        font-size: 12px;
        line-height: 31px;
        color: $color-text-grey;
    }
}
</style>
