<script>
import axios from 'axios';
import { store } from './store.js';
import HeaderComp from './components/HeaderComp.vue';
import MainComp from './components/MainComp.vue';
import { computed } from 'vue';

export default {
    name: "App",
    components: {
        HeaderComp,
        MainComp
    },
    data() {
        return {
            store
        };
    },

    created() {
    },

    computed: {
        searchArchetype() {
            if (!this.store.selected == "") {

                return axios.get(`https://db.ygoprodeck.com/api/v7/cardinfo.php?num=15&offset=0&archetype=${this.store.selected}`).then(response => {

                    this.store.arrayCarte = response.data.data;
                })
            }
        }
    }
}

</script>

<template>
    <HeaderComp @search="searchArchetype" />
    <MainComp />
</template>

<style lang="scss">
@use './style/main.scss';
</style>
