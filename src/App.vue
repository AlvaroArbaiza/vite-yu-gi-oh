<script>
import axios from 'axios';
import HeaderComp from './components/HeaderComp.vue';
import { store } from './store.js';

export default {
    name: "App",
    components: {
        HeaderComp
    },
    data() {
        return {
            store
        };
    },

    created() {
        axios.get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=15&offset=0").then(response => {
            console.log(response.data.data);
            this.store.arrayCarte = response.data.data;
            console.log(this.store.arrayCarte);
        })
    }
}

</script>

<template>
    <HeaderComp :test="'ciao'" />
</template>

<style lang="scss">
@use './style/main.scss';
</style>
