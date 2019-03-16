<template>
    <div>
        <Online v-if="view == 0"></Online>
        <Koszyk :koszyk="koszyk" v-if="view == 1"></Koszyk>
        <!--<div class="status" v-if="koszyk.length > 0">
            <span class="napis">Koszyk</span>
            <span class="ciemny">{{ sum }}</span>
        </div>
        -->
        <div class="komunikaty">
            <transition name="notify">
                <div class="notify" v-if="koszyk.length > 0" :class="notify ? 'notifycolor' : 'blu'" v-on:click="view = 1">
                    <div v-if="notify">Dodano do koszyka</div>
                    <div v-else>Koszyk</div>
                    </div>
            </transition>
            <!---->
        </div>
        
    </div>
</template>

<script>
import Online from './Online';
import Koszyk from './Koszyk';

import { setTimeout } from 'timers';

export default {
    components: {
        Online,
        Koszyk
    },
    data: function() { return {
        view: 0,
        koszyk: [],
        sum: 0,
        hajs: 0,
        notify: false
    }},
    methods: {
        add(data) {
            this.notify = true;
            setTimeout(() => {
                this.notify = false
            }, 1500)
            let yf = this.koszyk.find(x => x.name == data.nazwa);
            console.log(yf)
            if(yf) {
                yf.ilosc++;
                this.sum++;
                this.hajs += data.cena;
            } else {
                this.koszyk.push({
                    name: data.nazwa,
                    url: data.url,
                    wiecej: data.wiecej,
                    cena: data.cena,
                    ilosc: 1
                })
                this.sum++;
                this.hajs += (data.cena);
            }
            console.dir(this.koszyk)
        },
        remove(data) {
            let yf = this.koszyk.find(x => x.name == data.nazwa);
            if(yf.ilosc > 1) {
                yf.ilosc--;
                this.sum--;
                this.hajs -= yf.cena;
            } else {
                this.koszyk = this.koszyk.filter(x => x.name != data.nazwa);
                this.sum--;
                this.hajs -= data.cena;
            }
        }
    }
}
</script>

<style lang="scss" scoped>
    .komunikaty {
        position: fixed;
        flex-direction: column;
        display: flex;
        width: 300px;

        bottom: 0;
        right: 8px;
        z-index: 500;
    }

    .notify {
        margin: 10px;
        border-radius: 3px;
        padding: 15px 18px;
        font-size: 90%;
        font-weight: bold;
        user-select: none;
        color: white;
        transition: 500ms;
        background: #1d5cb2;
        box-shadow: 0 2px 4px rgba(0, 0, 0, 0.8);

        &:hover {
            background: #113669;
        }
    }

    .napis {
        transition: 200ms;
        border-top-left-radius: 5px;
        padding: 18px 32px;
        background: #1d5cb2;
    }
    .ciemny {
        border-top-right-radius: 5px;
        background: #113669;
        box-sizing: border-box;
        padding: 18px 32px; 
    }

    .notifycolor {
        background: #202124;
    }

    // transitions
    .notify-enter-active, .notify-leave-active {
        transition: .3s;
    }

    .notify-enter, .notify-leave-to {
        transform: scale(0.8);
        opacity: 0;
    }
</style>
