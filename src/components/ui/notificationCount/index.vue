<template>
    <a class="ui-notification-count">
        <div class="ui-notification-count__container">
            <div v-if="notificationCounter > 0"  class="ui-notification-count__counter">{{ notificationCounter }}</div>
            <IconsNotification class="ui-notification-count__icon"/>
        </div>
    </a>
</template>

<script>
export default {name: 'UiNotificationCount'}
</script>

<script setup>
import IconsNotification from '../../icons/notification/index.vue'

const props = defineProps({
    notificationCounter: {
        type: Number,
        default: 0
    }
})
</script>

<style lang="scss" scoped>
.ui-notification-count {
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
        justify-content: center;
        align-items: center;
        min-width: 20px;
        height: 20px;
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
