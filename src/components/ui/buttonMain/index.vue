<template>
    <button
        class="ui-btn-main"
        type="button"
        :class="classes"
        @click="emits('click')"
    >
        <slot/>
    </button>
</template>

<script>
export default {name: 'UiBtnMain'}
</script>

<script setup>
import {computed} from 'vue'

const emits = defineEmits(['click']);

const props = defineProps({
    size: {
        type: String,
        default: 'large'
    },
    themeSecondary: {
        type: Boolean,
        default: false
    }
})

const classes = computed(() => {
    return {
        [`ui-btn-main-size--${props.size}`]: true,
        [`ui-btn-main-theme--secondary`]: props.themeSecondary,
    }
})
</script>

<style lang="scss" scoped>
.ui-btn-main {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    background-color: $color-main-blue;
    color: $color-snow;
    transition-duration: 0.3s;

    &:hover {
        background-color: rgba(52, 120, 246, 0.81);
    }

    &:active {
        background-color: rgba(52, 120, 246, 0.6);
    }

    &.ui-btn-main-size--large {
        height: 48px;
        font-weight: 600;
        font-size: 16px;
        line-height: 1;
        border-radius: 12px;
    }

    &.ui-btn-main-size--medium {
        height: 34px;
        font-family: $mulish-font;
        font-weight: 600;
        font-size: 16px;
        line-height: 1;
        border-radius: 6px;
    }

    &.ui-btn-main-theme--secondary {
        background-color: $color-light-btn-grey;
        color: $color-general-dark;

        &:hover {
            background-color: rgba(236, 242, 255, 0.8);
        }

        &:active {
            background-color: rgba(236, 242, 255, 0.6);
        }
    }
}
</style>
