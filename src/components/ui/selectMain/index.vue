<template>
    <div class="ui-select" :class="classes" tabindex="0" :data-select="data.id">
        <fieldset>
            <legend> How long will it take</legend>

            <!--            <div class="ui-select__select">-->
            <div
                class="ui-select__selected"
                @click="data.isOpen = !data.isOpen"
            >
                <div class="ui-select__selected-value">
                    <div
                        class="ui-select__selected-text"
                        v-if="modelValue.time"
                    >
                        {{ modelValue.time }}
                    </div>
                </div>

                <div class="ui-select__selected-arrow">
                    <IconsArrowDown/>
                </div>
            </div>

            <div class="ui-select__items" ref="itemsRef">
                <div class="ui-select__items-wrap">
                    <div
                        class="ui-select__item"
                        v-for="(option, i) in options"
                        :key="i"
                        @click="selectItem(option)"
                    >
                        <div class="ui-select__item-text">
                            {{ option.time }}
                        </div>
                    </div>
                </div>
            </div>
            <!--            </div>-->
        </fieldset>
    </div>
</template>

<script>
export default {name: 'UiSelectMain'}
</script>

<script setup>
import {computed, onMounted, onUnmounted, reactive, ref} from 'vue'
import IconsArrowDown from '../../icons/IconArrowDown/index.vue'

const props = defineProps({
        modelValue: {
            time: '122'
        },
        options: {
            time: ''
        }
    }
)

const emits = defineEmits(['update:modelValue'])

const itemsRef = ref(null)

const data = reactive({
    isOpen: false,
})

const classes = computed(() => {
    return {
        [`ui-select--selected`]: props.modelValue.value,
        [`ui-select--active`]: data.isOpen,
        [`ui-select--scroll`]: props.options?.length >= 6,
    }
})

const selectItem = (option) => {
    emits('update:modelValue', option)
    data.isOpen = false
}

const closeHandler = (e) => {
    const select = e.target.closest(`[data-select="${data.id}"]`)
    if (!select) {
        data.isOpen = false
    }
}

onMounted(() => {
    document.addEventListener('click', closeHandler)
})

onUnmounted(() => {
    document.removeEventListener('click', closeHandler)
})
</script>

<style lang="scss">
.ui-select {
    max-width: 268px;
    width: 100%;

    &__select {
        position: relative;
        background-color: $color-snow;
        border-radius: 12px;
        transition-duration: 0.3s;
        transition-property: opacity, border-color;
        font-weight: 500;
        width: 100%;
        min-height: 44px;
    }

    &__selected {
        font-size: 16px;
        line-height: 24px;
        display: flex;
        align-items: center;
        min-height: inherit;
        justify-content: space-between;
        padding: 10px 20px 10px 16px;
        user-select: none;
        cursor: pointer;
        color: rgba($color-secondary-dark, 0.5);
        border-radius: 12px;
        position: relative;
        transition-duration: 0.3s;
        transition-property: border-color;
        border: none;

        &-name {
            padding-right: 16px;
        }

        &-text {
            font-weight: 500;
            font-size: 13px;
            line-height: 1.2;
            padding-right: 16px;
            color: rgba($color-secondary-dark, 0.8);
        }

        &-arrow {
            display: inline-flex;
            color: $color-light-blue;
            transition-property: transform;
            transition-duration: 0.3s;
        }

        &-value {
            display: flex;
            align-items: center;
        }

        &::before {
            content: '';
            position: absolute;
            width: 88.7%;
            left: 50%;
            transform: translateX(-50%);
            height: 1px;
            background-color: rgba($color-text-grey, 0.2);
            bottom: 0;
            transition-duration: 0.3s;
            opacity: 0;
        }
    }

    &:hover:not(.ui-select--active) {
        .ui-select__select {
            border-color: rgba($color-text-grey, 0.9);
        }
    }

    &__items {
        background-color: $color-snow;
        z-index: 9;
        border-radius: 0 0 12px 12px;
        border-top: 0;
        position: absolute;
        visibility: hidden;
        opacity: 0;
        left: 0;
        width: 100%;
        border-right: 1px solid transparent;
        border-left: 1px solid transparent;
        border-bottom: 1px solid transparent;

        &::-webkit-scrollbar {
            display: none;
        }

        &::-webkit-scrollbar-thumb {
            display: none;
        }

        &:empty {
            padding: 0;
        }

        &-wrap {
            padding: 11px 0;
            overflow-y: auto;
            max-height: 200px;

            &::-webkit-scrollbar {
                width: 4px;
                background-color: transparent;
                overflow: hidden;
                border-radius: 10px;
            }

            &::-webkit-scrollbar-thumb {
                border: 4px solid transparent;
                border-radius: 8px;
                background-clip: padding-box;
            }
        }
    }

    &__item {
        display: flex;
        cursor: pointer;
        align-items: center;
        padding: 0 10px 0 12px;
        user-select: none;
        transition-duration: 0.3s;
        transition-property: background-color;
        min-height: 35px;

        &:hover {
            background-color: rgba($color-light-blue, 0.03);
        }

        &:active {
            color: $color-light-blue;
        }

        &-name {
            font-size: 14px;
        }

        &-text {
            font-weight: 500;
            font-size: 11px;
            color: rgba($color-light-blue, 0.8);
            padding: 0 16px;
        }
    }

    &--active {
        .ui-select__selected {
            border-bottom-color: transparent;
            border-radius: 12px 12px 0 0;
            border-color: $color-light-blue;
            border-bottom: 0;

            &-arrow {
                transform: scale(-1);
            }

            &:before {
                opacity: 1;
            }
        }

        .ui-select__items {
            visibility: visible;
            opacity: 1;
            transition-duration: 0.2s;
            border-color: $color-light-blue;
        }
    }

    &--selected {
        .ui-select__selected {
            color: $color-general-dark;
        }
    }

    &--disabled-selected {
        pointer-events: none;

        .ui-select__selected {
            border-color: rgba($color-text-grey, 0.25);

            &-arrow {
                color: rgba($color-text-grey, 0.4);
            }
        }
    }

    &--scroll {
        .ui-select__items {
            overflow-y: scroll;
        }
    }
}
</style>

