<script>
export default {
    name: 'CardComp',
    props: ['card']
}
</script>

<template>
    <div class="cardYugi text-center">
        <div class="container_card">

            <img :src="card.card_images[0].image_url" :alt="card.name">
            <h5>{{ card.name }}</h5>
            <h6>{{ card.archetype }}</h6>
        </div>
    </div>
</template>

<style lang="scss" scoped>
@use '../../src/style/partials/_mixin.scss' as *;

.cardYugi {
    flex-basis: calc(100% / 5 - 0.8rem);

    .container_card {
        height: 100%;
        background-color: #d48f38;

        img {
            margin-bottom: 0.8rem;
        }

        h5 {
            color: #fff;
        }
    }
}
</style>