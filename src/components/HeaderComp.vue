<script>
export default {
    name: 'HeaderComp'
}
</script>

<template>
    <header>

        <div class="container d-flex align-items-center">

            <div id="logo">
                <img src="/img/yu-gi-oh_logo.png" alt="logo yu-gi-oh">
            </div>

            <div id="title">
                <h1>Yu-Gi-Oh Api</h1>
            </div>
        </div>

    </header>
</template>

<style lang="scss" scoped>
@use '../../src/style/partials/_mixin.scss' as *;

header {
    width: 100%;

    .container {
        width: 90%;
        height: 90px;

        #logo {
            flex-basis: 10%;
            margin-right: 1rem;
        }


    }
}
</style>