<template>
    <div>
        <div class="baner">
            <img class="btm" src="../assets/dostawa.png">
            <span class="motywacja">Nie dowieziemy na twój adres.</span>
            <input class="falowiec" type="text" placeholder="Wprowadź adres">
        </div>
        <div class="kat" v-for="(kat, i) in kategorie" :key="i">
            <div class="topp" style="flex-basis: 10%;">
                <img v-bind:src="kat.icon">
                <span class="kat-a">{{ kat.name }}</span>
            </div>
            <div class="topp oferty">
                <Oferta v-for="(oferta, i) in produkty(kat.id)" v-bind:key="i" v-bind:data="oferta"></Oferta>
            </div>
        </div>
        <div>
            <img class="btm" src="../assets/store.png">
            <span class="motywacja">Po więcej zakupów zapraszamy do sklepów</span>
        </div>
        
    </div>
</template>

<script>
import Oferta from './Oferta';
import Candy from '../assets/candy.png';
import Gotowe from '../assets/noodles.png';
import Nabial from '../assets/milk.png';
import Napoje from '../assets/water.png'

export default {
    components: {
        Oferta
    },
    beforeMount: function() {
        window.scrollTo({top: 0})
    },
    data: function() { return {
        kategorie: [
            {
                id: 0,
                name: "Słodycze",
                icon: Candy
            },
            {
                id: 1,
                name: "Nabiał",
                icon: Nabial
            },
            {
                id: 2,
                name: "Dania gotowe",
                icon: Gotowe
            },
            {
                id: 3,
                name: "Napoje",
                icon: Napoje
            }
        ],
        products: [
            {
                    kat: 0,
                    url: 'https://image.ceneostatic.pl/data/products/10890296/i-gerard-pryncypalki-235g.jpg',
                    nazwa: "kurła Pryncypałki",
                    wiecej: "235g",
                    cena: 4.49
                },
                {
                    kat: 0,
                    url: 'https://image.handelextra.pl/articles/220419_handel-extra_1_jpg_prince-polo.jpg',
                    nazwa: "Prince Polo kokosowe",
                    wiecej: "52g",
                    cena: 1.19
                },
                {
                    kat: 0,
                    url: 'https://secure.ce-tescoassets.com/assets/PL/415/5901588057415/ShotType1_540x540.jpg',
                    nazwa: "Wedel Ptasie Mleczko czekoladowe",
                    wiecej: "380g",
                    cena: 10.99
                },
                {
                    kat: 0,
                    url: 'https://www.scrummy.pl/830-large_default/golden-oreo.jpg',
                    nazwa: "Oreo Golden",
                    wiecej: "154g",
                    cena: 10.99
                },
                {
                    kat: 1,
                    url: "http://www.maluta.galeo.pro/media/p/73.jpg",
                    nazwa: "MALUTA Śmietana 18%",
                    wiecej: "200g",
                    cena: 1.59
                },
                {
                    kat: 1,
                    nazwa: 'Mleko UHT Twój Kubek 3,2%', 
                    wiecej: '1l', 
                    cena: 1.99,
                    url: 'http://www.mlekovita.com.pl/media/cache/product_view/uploads/products/401/prod_153.jpg'
                },
                {
                    kat: 1,
                    url: 'https://image.ceneostatic.pl/data/products/41203291/i-mlekpol-mazurski-smak-twarog-poltlusty-250-g.jpg',
                    nazwa: "Mlekpol Mazurski Smak twaróg półtłusty",
                    cena: 3.19,
                    wiecej: "250g"
                },
                {
                    kat: 1,
                    url: 'http://www.maluta.galeo.pro/media/p/124.jpg',
                    nazwa: "MALUTA Masło extra",
                    cena: 7.69,
                    wiecej: "200g"
                },
                {
                    kat: 2,
                    url: 'https://7.allegroimg.com/s512/033106/4a2f7ef34a5caa07aa5a7cb06c67',
                    nazwa: "Vifon Kurczak Curry",
                    wiecej: "70g",
                    cena: 0.99
                },
                {
                    kat: 2,
                    url: 'https://sgfm.elcorteingles.es/SGFM/dctm/MEDIA03/201607/13/00118032900054____2__600x600.jpg',
                    nazwa: "Carretilla Paella Marinera",
                    wiecej: "250g",
                    cena: 6.99
                }, 
                {
                    kat: 2,
                    url: 'https://secure.ce-tescoassets.com/assets/PL/921/5900477000921/ShotType1_540x540.jpg',
                    nazwa: "Hortex Zupa jarzynowa",
                    wiecej: "450g",
                    cena: 4.99
                },
                {
                    kat: 2,
                    url: 'https://secure.ce-tescoassets.com/assets/PL/007/5905009025007/ShotType1_540x540.jpg',
                    nazwa: "Złote paluszki rybne",
                    wiecej: "300g",
                    cena: 9.99
                },
                {
                    kat: 3,
                    url: 'https://zakupycodzienne.carrefour.pl/images/product/350x350/zywiec-zdroj-woda-niegazowana-15-l-ci0shl.jpg',
                    nazwa: "Woda niegazowana Żywiec Zdrój",
                    wiecej: "1.5l",
                    cena: 1.29
                },
                {
                    kat: 3,
                    url: 'https://www.dollargeneral.com/media/catalog/product/cache/image/700x700/e9c3970ab036de70892d86c6d221abfe/0/0/00012000809941_1.jpg',
                    nazwa: "Bepis",
                    wiecej: "330ml",
                    cena: 1.69
                },
                {
                    kat: 3,
                    url: 'https://images-na.ssl-images-amazon.com/images/G/01/aplusautomation/vendorimages/9acf4bf6-9b8f-4dbc-97fe-034459d5ee3c.png._CB276149877_.png',
                    nazwa: "Monster Energy",
                    cena: 4.69,
                    wiecej: "500ml"
                }
        ]
    }
    
    },
    methods: {
        produkty(katId) {
            return this.products.filter(p => p.kat == katId);
        },
        add(data) {
            this.$parent.add(data);
        }
    },
}
</script>

<style lang="scss" scoped>
    .komunikat {
        margin: 20px;
    }
    .motywacja {
        padding: 15px;
        font-size: 2em;
        font-weight: bold;
        display: block;
        color: #333333;
        text-align: center;
    }
    .baner {
        background: #e6e7eb;
        color: #333333;
        padding: 20px;
    }

    .btm {
        display: block;
        margin: auto;
        width: 50px;
    }

    .falowiec {
        background: white;
        font-family: inherit;
        border: none;
        border-radius: 5px;
        outline: none;
        padding: 15px 18px;
        width: 30%;
        margin: auto;
        color: #4e4e4e;
        display: block;
        font-size: 1em;
        box-shadow: 0 1px 2px rgba(0,0,0,0.12);
    }

    .koszyk {
        position: sticky;
        top: 0;
        background: #1d5cb2;
        color: white;
        font-weight: bold;
        padding: 20px;
        text-align: center;
    }
    .kat {
        border-top: 0.3px solid #e6e7eb;
        display: flex;
    }

    .kat-a {
        display: block;
        padding: 5px;
        font-size: 1.5em;
        font-weight: bold;
    }

    .topp {
        padding: 15px;
        color: #333333;
        img {
            padding: 5px;
            height: 50px;
        }
    }

    .oferty {
        display: flex;
        flex-basis: 90%;
    }
</style>