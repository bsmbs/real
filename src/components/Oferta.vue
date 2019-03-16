<template>
    <div class="karta" :class="data.ns && !data.kosz ? 'border' : ''">
        <div class="img">
            <img v-bind:src="data.url">
        </div>
        <span class="nazwa">{{ data.nazwa }}</span>
        <div class="doln">
            <span class="waga">{{ data.wiecej }}</span>
            <span class="cena">{{ data.cena }}</span>
        </div>
        <div v-if="!data.ns" class="kliknij blo" @click="$parent.add(data)">Dodaj do koszyka</div>
        <div v-if="data.kosz" class="kliknij red" @click="$parent.remove(data)">Usuń z koszyka</div>
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

        & > .kliknij {
            display: block;
        }
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
        border-top-left-radius: 5px;
        border-top-right-radius: 5px;
        margin: 5px;
    }
    .nazwa {
        display: block;
        padding: 10px;
        font-size: 110%;
        height: 25px;
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

    .kliknij {
        position: absolute;
        box-shadow: 0 10px 20px rgba(0,0,0,0.19), 0 6px 6px rgba(0,0,0,0.23);
        transition: 200ms;
        display: none;
        left: 0;
        right: 0;
        color: white;
        border-bottom-left-radius: 5px;
        border-bottom-right-radius: 5px;
        padding: 15px;
        font-weight: bold;
        font-size: 90%;

        &:hover {
        }
    }

    .blo {
        background: #1d5cb2;

        &:hover {
            background: #113669;
        }
    }

    .red {
        background: #c23329;
        
        
        &:hover {
            background: #88241d;
        }
    }

    .border {
        border-radius: 5px;
    }
</style>
