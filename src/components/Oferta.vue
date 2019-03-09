<template>
    <div class="karta">
        <div class="img">
            <img v-bind:src="data.url">
        </div>
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
        transform: scale(1.1);
        box-shadow: 0 10px 20px rgba(0,0,0,0.19), 0 6px 6px rgba(0,0,0,0.23);
        z-index: 2;
    }
    .img {
        display: block;
        height: 200px;
        margin: 10px;
        background: white;
        text-align: center;
        border-top-left-radius: 5px;
        border-top-right-radius: 5px;
        //border-radius: 15px;
    }
    .img img {
        margin: auto;
        height: 200px;
        max-width: 100%;
        max-height: 100%;
        object-fit: contain;
        border-top-left-radius: 5px;
        border-top-right-radius: 5px;
    }
    .karta {
        width: 100%;
        text-align: center;
        position: relative;
        user-select: none;
        transition: 200ms;
        display: inline-block;
        background: white;
        border-radius: 5px;
        margin: 5px;
    }
    .nazwa {
        display: block;
        padding: 10px;
        font-size: 110%;
        color: #333333;
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
        color: #333333;
    }
</style>
