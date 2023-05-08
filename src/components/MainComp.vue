<script>
import CardComp from '../components/CardComp.vue';
import AnimationComp from '../components/AnimationComp.vue';
import { store } from '../store.js';

export default {
    name: 'MainComp',
    components: {
        CardComp,
        AnimationComp
    },
    data() {
        return {
            store
        };
    }
}
</script>

<template>
    <main class="py-4">

        <!-- select -->
        <div class="container cont-select">
            <select class="form-select" name="archetype" id="archetype" v-model="store.selected" @click="$emit('search')">
                <option selected disabled value="">Scegli l'archetipo</option>

            </select>
        </div>

        <!-- container white -->
        <div class="container-white">

            <!-- cards found -->
            <div class="container d-flex align-items-center ps-2" id="cards-found">
                <span>Found {{ store.arrayCarte.length }} cards</span>
            </div>

            <!-- loader -->
            <div v-if="store.animat == true" class="container">
                <AnimationComp />
            </div>

            <!-- cards -->
            <div v-else class="container d-flex container-cards">

                <CardComp v-for="(elem, index) in store.arrayCarte" :key="index" :card="elem" />
            </div>
        </div>


    </main>
</template>

<style lang="scss" scoped>
@use '../../src/style/partials/_mixin.scss' as *;
@use '../style/partials/_variables.scss' as *;

main {
    width: 100%;
    background-color: $bg-sand;

    .container {
        margin: 0;
        padding: 0;
    }

    // select 
    .cont-select {
        width: 80%;
        margin: 0 auto 1rem;

        #archetype {
            width: 11rem;
        }
    }

    // container bg white
    .container-white {
        padding: 2.5rem;
        width: 80%;
        margin: 0 auto;
        background-color: #fff;

        // cards found 
        #cards-found {
            height: 3rem;
            color: #fff;
            background-color: $bg-black;
        }

        // container cards
        .container-cards {
            gap: 1rem;
            flex-wrap: wrap;
        }
    }
}
</style>