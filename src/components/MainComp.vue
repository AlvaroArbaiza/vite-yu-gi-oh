<script>
import CardComp from '../components/CardComp.vue';
import { store } from '../store.js';

export default {
    name: 'MainComp',
    components: {
        CardComp
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
                <option value="Alien">Alien</option>
                <option value='"C"'>"C"</option>
                <option value="-Eyes Dragon">-Eyes Dragon</option>
                <option value="@Ignister">@Ignister</option>
                <option value="A.I.">A.I.</option>
                <option value="ABC">ABC</option>
                <option value="Abyss Actor">Abyss Actor</option>
                <option value="Abyss Script">Abyss Script</option>
                <option value="Adamancipator">Adamancipator</option>
                <option value="Advanced Crystal Beast">Advanced Crystal Beast</option>
                <option value="Adventurer Token">Adventurer Token</option>
                <option value="Aesir">Aesir</option>
                <option value="Aether">Aether</option>
                <option value="Albaz Dragon">Albaz Dragon</option>
            </select>
        </div>

        <!-- container white -->
        <div class="container-white">

            <!-- cards found -->
            <div class="container d-flex align-items-center ps-2" id="cards-found">
                <span>Found {{ store.arrayCarte.length }} cards</span>
            </div>

            <!-- cards -->
            <div class="container d-flex container-cards">

                <CardComp v-for="(elem, index) in store.arrayCarte" :key="index" :card="elem" />
            </div>
        </div>


    </main>
</template>

<style lang="scss" scoped>
@use '../../src/style/partials/_mixin.scss' as *;

main {
    width: 100%;
    background-color: #d48f38;

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
            background-color: #212529;
        }

        // container cards
        .container-cards {
            gap: 1rem;
            flex-wrap: wrap;
        }
    }
}
</style>