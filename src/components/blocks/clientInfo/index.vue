<template>
    <div class="blocks-client-info" @click="emits('click')">
        <img class="blocks-client-info__icon" :src="clientIcon" alt="user logo">

        <div class="blocks-client-info__box">
            <a class="blocks-client-info__title">{{clientName}}</a>
            <span class="blocks-client-info__role">{{clientRole}}</span>
        </div>

        <div class="blocks-client-info__box">
            <a class="blocks-client-info__title">{{clientName}}</a>
            <span class="blocks-client-info__role">{{clientRole}}</span>
        </div>
    </div>
</template>

<script>
export default {name: 'BlocksClientInfo'}
</script>

<script setup>
const props = defineProps({
    clientName: {
        type: String,
        default: 'Client Name'
    },
    clientRole: {
        type: String,
        default: 'Client role'
    },
    clientIcon: {
        type: String,
        default: './src/assets/images/empty-user-icon.svg'
    },
})

const emits = defineEmits(['click'])
</script>

<style lang="scss" scoped>
.blocks-client-info {
    display: flex;
    align-items: center;
    gap: 18px;
    cursor: pointer;

    &__box {
        display: flex;
        flex-direction: column;
        gap: 4px;
    }

    &__title {
        font-family: $montserrat-font;
        font-weight: 700;
        font-size: 15px;
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
        width: 54px;
        height: 54px;
        border-radius: 100px;
    }
}

</style>
