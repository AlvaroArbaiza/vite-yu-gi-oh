<script>
export default {
    name: 'AnimationComp'
}
</script>

<template>
    <div class="animation row align-items-center justify-content-center m-0">

        <div>
            <span>s</span>
            <span>c</span>
            <span>e</span>
            <span>g</span>
            <span>l</span>
            <span>i</span>
            <span>!</span>
        </div>
    </div>
</template>

<style lang="scss" scoped>
@use '../../src/style/partials/_mixin.scss' as *;
@use '../style/partials/_variables.scss' as *;



.animation {
    display: flex;
    width: 100%;
    height: 300px;
    background: black;
    align-items: center;
    justify-content: center;

    div {
        text-align: center;
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 2rem;

        span {
            display: inline-block;
            text-transform: uppercase;
            text-align: center;
            font-size: 4em;
            font-family: arial;
            font-weight: 600;
            transform: scale(.5);
            color: $animation-black;
        }
    }
}


span:nth-child(1) {
    animation: $effect;
}

span:nth-child(2) {
    animation: $effect .2s;
}

span:nth-child(3) {
    animation: $effect .3s;
}

span:nth-child(4) {
    animation: $effect .4s;
}

span:nth-child(5) {
    animation: $effect .5s;
}

span:nth-child(6) {
    animation: $effect .6s;
}

span:nth-child(7) {
    animation: $effect .7s;
}

@keyframes hover {
    0% {
        transform: scale(1);
        color: $animation-black;
        -webkit-text-stroke: 2px gray;
    }

    50% {
        transform: scale(2);
        color: pink;
        -webkit-text-stroke: 3px red;
        filter: drop-shadow(0 0 1px black)drop-shadow(0 0 1px black)drop-shadow(0 0 3px red)drop-shadow(0 0 5px red)hue-rotate(10turn);
    }

    100% {
        transform: scale(1);
        color: $animation-black;
        -webkit-text-stroke: 2px gray;
    }


}
</style>