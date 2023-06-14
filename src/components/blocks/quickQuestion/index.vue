<template>
    <div class="blocks-quick-question">
        <div v-if="!data.isSent" class="blocks-quick-question__initial">
            <div class="blocks-quick-question__top">
                <IconsQuestion class="blocks-quick-question__icon"/>

                <p class="blocks-quick-question__text">Quick question</p>
            </div>

            <div class="blocks-quick-question__input-box">
                <input class="blocks-quick-question__input" type="text">

                <UiBtnMain
                    class="blocks-quick-question__btn"
                    :size="data.size"
                    @click="data.isSent = true"
                >
                    Send
                </UiBtnMain>
            </div>
        </div>

        <div v-else class="blocks-quick-question__is-sent">
            <div class="blocks-quick-question__is-sent-box">
                <IconSuccess class="blocks-quick-question__is-sent-icon"/>

                <p class="blocks-quick-question__is-sent-text">Message sent.</p>
            </div>

            <UiBtnMain
                :size="data.size"
                themeSecondary
            >
                See conversation
            </UiBtnMain>
        </div>
    </div>
</template>

<script>
export default {name: 'BlocksQuickQuestion'}
</script>

<script setup>
import IconsQuestion from '../../icons/question/index.vue'
import UiBtnMain from '../../ui/buttonMain/index.vue'
import {reactive} from 'vue'
import IconSuccess from '../../icons/success/index.vue'

const data = reactive({
    size: 'medium',
    isSent: false,
})
</script>

<style lang="scss" scoped>
.blocks-quick-question {
    padding: 16px 14px;
    box-shadow: 0 6px 26px rgba(0, 0, 0, 0.08);
    border-radius: 8px;

    &__top {
        display: flex;
        gap: 10px;
        align-items: center;
    }

    &__icon {
        color: $color-main-blue;
    }

    &__text {
        font-family: $montserrat-font;
        font-weight: 500;
        font-size: 15px;
        line-height: 18px;
    }

    &__input-box {
        display: flex;
        gap: 10px;
        margin-top: 14px;
    }

    &__input {
        flex-grow: 3;
        height: 34px;
        border-radius: 21px;
        width: 100%;
        padding: 0 14px;
        border: none;
        outline: none;
        font-size: 16px;
        line-height: 24px;
        font-weight: 400;
        background-color: $color-light-grey;
    }

    &__btn {
        flex-basis: 20%;
    }

    &__is-sent {
        display: flex;
        flex-direction: column;
        gap: 12px;

        &-box {
            display: flex;
            gap: 10px;
            align-items: center;
        }

        &-icon {
            width: 19px;
            height: 19px;
        }

        &-text {
            font-weight: 500;
            font-size: 15px;
            line-height: 1;
        }
    }
}
</style>
