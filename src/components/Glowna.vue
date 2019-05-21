<template>
    <div>
        <div class="prezentacje">
            <div class="prezentacja">
                <div class="obrazek">
                    <img src="https://www.getraenke-hoffmann.de/sites/default/files/2018-09/gh_payback_karte.jpg">
                </div>
                <div class="opis">
                    <h1>Podaruj komuś prezent</h1>
                    <h3>Za kartę podarunkową real ,- można kupić wszystko w naszym sklepie. To nie może być nietrafiony prezent!</h3>
                    <div class="oferty">
                        <Oferta v-bind:data="{id: 0, nazwa: 'Eksluzywne krzesło na balkon', wiecej: '...albo ogród', cena: '66.99zł', url: 'https://www.twojpasaz.pl/userdata/gfx/b0580bfdd8ef51d31b8dcccba5da3146.jpg', ns: true}"></Oferta>
                        <Oferta v-bind:data="{id: 0, nazwa: 'KFC kubełek', wiecej: 'We wtorki', cena: '9.99zł', url: 'https://kfc.pl/assets/img/domains/pl/homepage-image-bucket.png', ns: true}"></Oferta>
                    </div>
                </div>
            </div>
            <img class="lista-maly" src="../assets/real.png">
            <div class="prezentacja">
                <div class="obrazek">
                    <img v-bind:src="niskie">
                </div>
                <div class="opis">
                    <h1>Włączamy niskie ceny! w realu ,-</h1>
                    <h3>Najniższe ceny na rynku znajdziesz właśnie w sklepach real ,-! Zapraszamy do zakupów</h3>
                </div>
            </div>
            <!--<div class="oferty">
                <Oferta v-bind:key="oferta.id" v-for="oferta in oferty" v-bind:data="oferta"></Oferta>
            </div>-->
            <div class="odkryj" v-on:click="$parent.current = 'Zakupy'">Zrób zakupy!</div>
        </div>
    </div>
</template>

<script>
    import Niskie from '../assets/niskie.png';
    import Oferta from './Oferta';
    export default {
        components: {
            Oferta
        },
        data: function () {
            return {
                niskie: Niskie,
                oferty: [{
                    id: 0,
                    url: 'https://res.cloudinary.com/dj484tw6k/f_auto,q_auto,c_pad,b_white,w_360,h_360/v1507259978/bb/6995.png',
                    nazwa: "Chipsy Lays zielona cebulka",
                    wiecej: "150g",
                    cena: "3.49zł",
                    ns: true
                }, {
                    id: 1,
                    url: 'https://www.ezebra.pl/pol_pl_KTC-OLEJ-PALMOWY-CZYSTY-NATURALNY-KOSMETYK-500ML-1237_1.jpg',
                    nazwa: "Olej palmowy",
                    wiecej: "500ml",
                    cena: "10.49zł",
                    ns: true
                }, {
                    id: 2,
                    url: 'https://sgfm.elcorteingles.es/SGFM/dctm/MEDIA03/201607/13/00118032900054____2__600x600.jpg',
                    nazwa: "Paella do mikrofali",
                    wiecej: "250g",
                    cena: "6.99zł",
                    ns: true
                }, {
                    id: 3,
                    url: 'http://www.maluta.galeo.pro/media/p/74.jpg',
                    nazwa: "Śmietana 18% maluta",
                    wiecej: "400g",
                    cena: "3.99zł",
                    ns: true
                }]
            }
        },
        methods: {
            open: function (lnk) {
                window.location.href = lnk
            }
        }
    }
</script>

<style lang="scss">
    .prezentacje {
        display: flex;
        flex-direction: column;
    }
    .prezentacja {
        display: flex;
    }

    .obrazek img{
        max-width: 100%;
        max-height: 300px;
    }

    .opis {
        margin: 20px;
    }

    .lista {
        background: #e6e7eb;
        color: #333333;
    }

    .lista-tytul {
        display: block;
        font-weight: 1000;
        text-align: center;
        padding: 15px;
        font-size: 180%;
    }

    .lista-maly {
        margin: auto;
        display: block;
        width: 100px;
        padding: 25px;
    }

    .oferty {
        display: flex;
        margin: 0 20px;
        flex-direction: column;
    }

    .odkryj {
        cursor: pointer;
        margin: 20px;
        text-align: center;
        display: block;
        user-select: none;
        border-bottom-left-radius: 128487px;
        border-top-left-radius: 128487px;
        border-top-right-radius: 128487px;
        border-bottom-right-radius: 128487px;
        background: #1d5cb2;
        color: white;
        padding: 18px 32px;
        font-weight: bold;
        font-size: 90%;
        transition: 300ms;

        &:hover {
            background: #113669;
        }
    }
    
    @media screen and (min-width: 768px) {

    }

    @media screen and (max-width: 768px) {
        .prezentacja {
            flex-direction: column;
        }

        .obrazek img {
            height: auto;
        }
    }

    @media screen and (min-width: 1024px) {
        .oferty { flex-direction: row; }
    }

    @media screen and (max-width: 1024px) {
            .oferty > * {
        margin: 10px auto;
        }
    }
    
</style>