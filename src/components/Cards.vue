
<template>
    <section class="container">
        <div class="row">
            <CardsComponent v-for="character in store.cardList" :key="character.id" :character="character" />
        </div>
    </section>
</template>

<script>
import { store } from '../data/data';
import CardsComponent from './CardsComponent.vue';
export default {
    name: 'Cards',
    components: {
        CardsComponent
    },
    data() {
        return {
            store
        }
    },
    methods: {
    }
}
</script>

<style lang="scss" scoped></style>