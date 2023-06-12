<script>
import { store } from "../store.js";
import SingleCard from './SingleCard.vue';

export default {
    name: 'CardsList',
    components: {
        SingleCard,
    },
    data() {
        return {
            store,
        }
    },
    computed: {
        cardsNumber() {
            return store.cardList.length;
        }
    }
}

</script>

<template>
    <section class="container bg-white mb-5 p-5">

        <div class="row justify-center">
            <div class="cardCounter p-2 text-white">Found {{ this.cardsNumber }} cards
                <span v-if="store.archSelect !== ''">with archetype {{ store.archSelect }}</span>
            </div>

            <!-- Cards -->
            <SingleCard v-for="singleCard in store.cardList" :key="singleCard.id" :details="singleCard" />
        </div>

    </section>
</template>

<style lang="scss" scoped>
.cardCounter {
    background-color: #212529;
}
</style>