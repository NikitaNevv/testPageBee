<template>
    <header class="section-header">
        <a class="section-header__logo" href="#">
            <img src="@/assets/images/logo.svg" alt="carbee logo icon">
            <img src="@/assets/images/text_carbee.svg" alt="brand name: carbee">
        </a>

        <div class="section-header__navigation">
            <a class="section-header__navigation-link" href="#">
                <IconsHome class="section-header__navigation-icon"/>
            </a>

            <a class="section-header__navigation-link" href="#">
                <IconsSearch class="section-header__navigation-icon"/>
            </a>

            <a class="section-header__navigation-link" href="#">
                <IconsDollar/>

            </a>

            <a class="section-header__navigation-link" href="#">
                <IconsCalendar class="section-header__navigation-icon"/>
            </a>

            <UiMessageCount
                class="section-header__navigation-link"
                :messageCounter="data.messageCounter"
            />

            <UiNotificationCount
                class="section-header__navigation-link"
                :notificationCounter="data.notificationCounter"
            />
        </div>

        <BlocksUserHeaderInfo
            :userName="data.userName"
            :userRole="data.userRole"
            :userIcon="data.userIcon"
        />
    </header>
</template>

<script>
import { reactive } from 'vue'

export default {name: 'SectionHeader'}

const data = reactive({
    messageCounter: 22,
    notificationCounter: 3,
    userName: 'Tech Way Auto',
    userRole: 'Mechanic',
    userIcon: './src/assets/images/userIcon.png',
})
</script>

<script setup>
import IconsHome from '../../icons/home/index.vue'
import IconsSearch from '../../icons/search/index.vue'
import IconsDollar from '../../icons/dollar/index.vue'
import IconsCalendar from '../../icons/calendar/index.vue'
import UiMessageCount from '../../ui/messagesCount/index.vue'
import UiNotificationCount from '../../ui/notificationCount/index.vue'
import BlocksUserHeaderInfo from '../../blocks/userHeaderInfo/index.vue'
</script>

<style lang="scss" scoped>
.section-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 70px;
    padding: 0 30px;

    &__logo {
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 6px;
    }

    &__navigation {
        display: flex;
        align-items: center;
        height: 100%;

        &-link {
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            height: 100%;
            width: 100px;
            color: $color-main-grey;
            transition-duration: 0.3s;

            &:after {
                content: '';
                position: absolute;
                width: 100%;
                transform: scaleX(0);
                height: 2px;
                bottom: 0;
                left: 0;
                background-color: $color-secondary-blue;
                transform-origin: bottom right;
                transition: transform 0.3s ease-out;
            }

            &:hover::after {
                transform: scaleX(1);
                transform-origin: bottom left;
            }

            &:hover {
                color: $color-secondary-blue;
            }

            &:active {
                color: rgba(15, 105, 221, 0.81);
            }
        }

        &-icon  {
            width: 24px;
            height: 27px;
        }
    }

    &__user {
        display: flex;
        gap: 10px;
    }
}
</style>
