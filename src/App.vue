<script>
import axios from 'axios';
import { store } from './store.js';
import HeaderComp from './components/HeaderComp.vue';
import MainComp from './components/MainComp.vue';

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
        axios.get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=15&offset=0&archetype=alien").then(response => {
            console.log(response.data.data);
            this.store.arrayCarte = response.data.data;
            console.log(this.store.arrayCarte);
        })
    }
}

</script>

<template>
    <HeaderComp />
    <MainComp />
</template>

<style lang="scss">
@use './style/main.scss';
</style>
