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

        // creazione di elementi options inseriti in base al numero di archetipi dell'api
        axios.get("https://db.ygoprodeck.com/api/v7/archetypes.php").then(response => {
            console.log(response.data);
            response.data.forEach((element, index) => {

                const select = document.getElementById('archetype');

                let option = document.createElement('option');
                option.value = element.archetype_name;
                option.textContent = element.archetype_name;
                select.appendChild(option);
            });
        })
    },

    computed: {
        searchArchetype() {

            store.animat = true;

            if (!store.selected == "") {

                store.animat = false;

                return axios.get(`https://db.ygoprodeck.com/api/v7/cardinfo.php?num=15&offset=0&archetype=${store.selected}`)
                    .then(response => {

                        store.arrayCarte = response.data.data;
                    })
                    .catch(function (error) {
                        console.log(error);
                    })
            }
        }
    }
}

</script>

<template>
    <div>

        <HeaderComp @search="searchArchetype" />
        <MainComp />
    </div>
</template>

<style lang="scss">
@use './style/main.scss';
</style>
