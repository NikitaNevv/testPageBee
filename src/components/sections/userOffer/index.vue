<template>
    <div class="sections-user-offer" :class="classes">
        <p class="sections-user-offer__title">Your Offer</p>

        <div class="sections-user-offer__input-box">
            <span class="sections-user-offer__currency">$</span>

            <input
                class="sections-user-offer__input"
                type="text"
                v-model="data.inputText"
                :size="inputSize"
                :placeholder="placeholderText"
                @mousedown="clearPlaceholder"
                @blur="resetPlaceholder"
            >
        </div>

        <div
            v-if="data.inputText < 400 && data.inputText"
            class="sections-user-offer__chances"
        >
            <IconsBadChancesSmile/>
            <p class="sections-user-offer__chances-text">Average chances</p>
        </div>

        <div
            v-if="data.inputText < 800 && data.inputText && data.inputText >= 400"
            class="sections-user-offer__chances"
        >
            <IconsGoodChancesSmile/>
            <p class="sections-user-offer__chances-text">Average chances</p>
        </div>

        <div
            v-if="data.inputText >= 800 && data.inputText"
            class="sections-user-offer__chances"
        >
            <IconsAverageChancesSmile/>
            <p class="sections-user-offer__chances-text">Average chances</p>
        </div>

        <UiSelectMain
            v-model="data.value"
            :options="data.options"
        />
    </div>
</template>

<script>
export default {name: 'SectionsUserOffer'}
</script>

<script setup>
import {computed, reactive, ref} from 'vue'
import IconsAverageChancesSmile from '../../icons/averageChancesSmile/index.vue'
import IconsBadChancesSmile from '../../icons/badChancesSmile/index.vue'
import IconsGoodChancesSmile from '../../icons/goodChancesSmile/index.vue'
import UiSelectMain from '../../ui/selectMain/index.vue'

const data = reactive({
    inputText: '',

    value: {time: 'Select time', value: 0,},
    options: [
        {
            time: '12',
            value: 1
        },
        {
            time: '22',
            value: 2
        },
        {
            time: '4',
            value: 3
        }
    ],
})

const inputSize = computed(() => {
    if (data.inputText.length === 0) {
        return 1
    }

    return data.inputText.length
})

const placeholderText = ref('0')

const clearPlaceholder = () => {
    placeholderText.value = ''
}

const resetPlaceholder = () => {
    if (!data.inputText) {
        placeholderText.value = '0'
    }
}

const classes = computed(() => {
    return {
        [`sections-user-offer--average`]: data.inputText >= 800 && data.inputText > 0,
        [`sections-user-offer--good`]: data.inputText < 800 && data.inputText > 0,
        [`sections-user-offer--bad`]: data.inputText < 400 && data.inputText > 0,
    }
})
</script>

<style lang="scss" scoped>
.sections-user-offer {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 398px;
    flex-shrink: 0;
    padding: 34px 40px 28px;
    box-shadow: 0 6px 26px rgba(0, 0, 0, 0.08);
    border-radius: 12px;

    &__title {
        font-weight: 600;
        font-size: 20px;
        line-height: 1;
    }

    &__input-box {
        display: flex;
        justify-content: center;
        align-items: start;
        margin-top: 38px;
        text-align: center;
        width: max-content;
    }

    &__currency {
        font-family: $mulish-font;
        color: $color-light-blue;
        font-weight: 700;
        font-size: 25px;
        line-height: 31px;
    }

    &__input {
        display: flex;
        font-family: $mulish-font;
        font-weight: 400;
        font-size: 80px;
        line-height: 100px;
        color: $color-light-blue;
        background-color: transparent;
        outline: none;
        border: none;
        text-align: center;
        max-width: 300px;

        &::placeholder {
            color: $color-light-blue;
            opacity: 1;
        }
    }

    &__chances {
        margin-top: 36px;
        display: flex;
        gap: 8px;

        &-text {
            font-weight: 500;
            font-size: 13px;
            line-height: 22px;
        }
    }

    &--average {
        .sections-user-offer__currency {
            color: $color-secondary-grey;
        }

        .sections-user-offer__input {
            color: $color-secondary-grey;
        }
    }

    &--good {
        .sections-user-offer__currency {
            color: $color-accent-positive;
        }

        .sections-user-offer__input {
            color: $color-accent-positive;
        }
    }

    &--bad {
        .sections-user-offer__currency {
            color: $color-accent-bad;
        }

        .sections-user-offer__input {
            color: $color-accent-bad;
        }
    }
}
</style>
