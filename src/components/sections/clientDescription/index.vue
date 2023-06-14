<template>
    <div class="section-client-options">
        <span class="section-client-options__title">Lexus RX 450h 2012</span>

        <span class="section-client-options__model">4 cyl. Hybrid A-Spec</span>

        <span class="section-client-options__comment">I dont know whats wrong with it, just need it to be fixed asap!</span>

        <div class="section-client-options__client-box">
            <BlocksClientInfo
                :clientName="data.clientName"
                :clientRole="data.clientRole"
                :clientIcon="data.clientIcon"
            />

            <UiBtnSecondary>Message</UiBtnSecondary>
        </div>

        <BlocksQuickQuestion class="section-client-options__quick-question"/>

        <BlocksOfferParameters class="section-client-options__offer-params"/>
    </div>
</template>

<script>
export default {name: 'SectionClientDescription'}
</script>

<script setup>
import BlocksClientInfo from '../../blocks/clientInfo/index.vue'
import UiBtnSecondary from '../../ui/buttonSecondary/index.vue'
import {reactive} from 'vue'
import BlocksQuickQuestion from '../../blocks/quickQuestion/index.vue'
import BlocksOfferParameters from '../../blocks/offerParameters/index.vue'

const data = reactive({
    clientName: 'Michael ',
    clientRole: 'Owner',
    clientIcon: './src/assets/images/clientIco.svg',
})
</script>

<style lang="scss" scoped>
.section-client-options {
    display: flex;
    flex-basis: 50%;

    flex-direction: column;
    font-family: $montserrat-font;

    &__title {
        font-weight: 600;
        font-size: 15px;
        line-height: 1;
    }

    &__model {
        font-family: $mulish-font;
        font-weight: 600;
        font-size: 12px;
        line-height: 31px;
        color: $color-text-grey;
    }

    &__comment {
        margin-top: 16px;
        font-weight: 500;
        font-size: 14px;
        line-height: 15px;
        color: $color-text-grey;
    }

    &__client-box {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-top: 34px;
    }

    &__quick-question {
        margin-top: 34px;
    }

    &__offer-params {
        margin-top: 50px;
    }
}
</style>
