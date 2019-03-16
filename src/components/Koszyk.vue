<template>
    <div>
        <div class="baner">
            <img class="btm" src="../assets/shopping-bag.png">
            <div class="motywacja">To twój koszyk</div>
        </div>
        <div class="longa" @click="$parent.view = 0">Wróć na zakupy</div>
        <div class="prods">
            <Oferta class="of" v-for="(p, i) in koszyk" v-bind:key="i" v-bind:data="{nazwa: p.name, wiecej: 'Ilość: '+p.ilosc, cena: (p.ilosc*p.cena).toFixed(2), url: p.url, ns: true, kosz: true}"></Oferta>
        </div>

        <div class="suma">Suma <span class="big">{{ $parent.hajs.toFixed(2) }}</span></div>
    </div>
</template>

<script>
import Oferta from './Oferta';

export default {
    props: ['koszyk'],
    components: {
        Oferta
    },
    methods: {
        remove(data) {
            this.$parent.remove(data);
        }
    }
}
</script>

<style lang="scss" scoped>
.btm {
    display: block;
    margin: auto;
    width: 50px;
}

.baner {
    background: #e6e7eb;
    color: #333333;
    padding: 20px;
}

.motywacja {
    padding: 15px;
    font-size: 2em;
    font-weight: bold;
    display: block;
    color: #333333;
    text-align: center;
}

.prods {
    margin: 20px;
}

.longa {
    background: #1d5cb2;
    text-align: center;
    font-weight: bold;
    user-select: none;
    padding: 20px;
    transition: 200ms;
    color: white;

    &:hover {
        background: #113669;
    }
}
.of {
    width: 250px;
}
.suma {
    padding: 20px;
    text-align: center;
    color: #333;
}

.big {
    font-size: 300%;
}
</style>

