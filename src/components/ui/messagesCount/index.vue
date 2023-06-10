<template>
    <a class="ui-message-count">
        <div class="ui-message-count__container">
            <div v-if="messageCounter > 0" class="ui-message-count__counter">{{ messageCounter }}</div>
            <IconsMessages class="ui-message-count__icon"/>
        </div>
    </a>
</template>

<script>
export default {name: 'UiMessageCount'}
</script>

<script setup>
import IconsMessages from '../../icons/messages/index.vue';

const props = defineProps({
    messageCounter: {
        type: Number,
        default: 0
    }
})
</script>

<style lang="scss" scoped>
.ui-message-count {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100%;
    cursor: pointer;

    &__container {
        position: relative;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    &__counter {
        position: absolute;
        top: -6px;
        right: -6px;
        display: flex;
        min-width: 20px;
        min-height: 20px;
        justify-content: center;
        align-items: center;
        padding: 2px 6px;
        font-weight: 500;
        font-size: 13px;
        background-color: $color-accent-negative;
        border-radius: 50px;
        letter-spacing: 0.2px;
        color: $color-snow;
    }

    &__icon {
        width: 32px;
        height: 24px;
    }
}
</style>
