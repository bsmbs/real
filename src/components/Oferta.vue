<template>
    <div class="karta">
        <img v-bind:src="data.url">
        <span class="nazwa">{{ data.nazwa }}</span>
        <div class="doln">
        <span class="waga">{{ data.wiecej }}</span>
        <span class="cena">{{ data.cena }}</span>
        </div>
    </div>
</template>

<script>
export default {
    props: ['data']
}
</script>

<style lang="scss">
    .karta:hover {
        background: #333333;
        color: white;
    }
    .karta img {
        display: block;
        height: 300px;
        max-width: 100%;
        border-radius: 15px;
    }
    .karta {
        transition: 200ms;
        display: inline-block;
        background: white;
        border-radius: 15px;
        margin: 5px;
    }
    .nazwa {
        display: block;
        padding: 10px;
        font-size: 110%;
    }
    .waga {
        padding-right: 10px;
        //padding: 10px;
        color: gray;
    }
    .doln {
        padding: 10px;
    }
    .cena {
        font-size: 150%;
    }
</style>
