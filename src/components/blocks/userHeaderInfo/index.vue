<template>
    <div class="blocks-user-header-info" @click="emits('click')">
        <div class="blocks-user-header-info__box">
            <span class="blocks-user-header-info__title">{{userName}}</span>
            <span class="blocks-user-header-info__role">{{userRole}}</span>
        </div>

        <img class="blocks-user-header-info__icon" :src="userIcon" alt="user logo">
    </div>
</template>

<script>
export default {name: 'BlocksUserHeaderInfo'}
</script>

<script setup >
const props = defineProps({
    userName: {
        type: String,
        default: 'User Name'
    },
    userRole: {
        type: String,
        default: 'Uer role'
    },
    userIcon: {
        type: String,
        default: './src/assets/images/empty-user-icon.svg'
    },
})

const emits = defineEmits(['click'])
</script>

<style lang="scss" scoped>
.blocks-user-header-info {
    display: flex;
    align-items: center;
    gap: 10px;
    cursor: pointer;

    &__box {
        display: flex;
        flex-direction: column;
        gap: 6px;
    }

    &__title {
        font-family: $mulish-font;
        font-weight: 700;
        font-size: 14px;
        line-height: 1;
    }

    &__role {
        font-family: $mulish-font;
        font-weight: 600;
        font-size: 14px;
        line-height: 1;
        color: $color-main-grey;
    }

    &__icon {
        width: 56px;
        height: 56px;
        border-radius: 100px;
    }
}
</style>
