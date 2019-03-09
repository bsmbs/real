<template>
    <div>
        <div class="prezentacje">
            <div class="prezentacja">
                <div class="obrazek">
                    <img src="https://www.real.de/typo3conf/ext/wfp2_real_giftcard/Resources/Public/Images/geschenkkarte.jpg">
                </div>
                <div class="opis">
                    <h1>Z kartą real ,- jeszcze tańsze zakupy</h1>
                    <h3>Na najbliższych zakupach załóż kartę real ,- a zakupy zrobisz jeszcze taniej</h3>
                    <div class="oferty">
                        <Oferta v-bind:data="{id: 0, nazwa: 'Telefon Xiaomi Mi 9', wiecej: '2199zł bez karty', cena: '1649zł', url: 'https://cdn.x-kom.pl/i/setup/images/prod/big/product-new-big,,2019/2/pr_2019_2_26_12_54_20_802_01.jpg'}"></Oferta>
                        <Oferta v-bind:data="{id: 0, nazwa: 'Mleko UHT Twój Kubek 3,2% 1l', wiecej: '2.99zł bez karty', cena: '1.99zł', url: 'http://www.mlekovita.com.pl/media/cache/product_view/uploads/products/401/prod_153.jpg'}"></Oferta>
                    </div>
                </div>
            </div>
        </div>
        <div class="lista">
            <img class="lista-maly" src="../assets/real.png">
            <span class="lista-tytul">Oferty real ,-</span>
            <div class="oferty">
                <Oferta v-bind:key="oferta.id" v-for="oferta in oferty" v-bind:data="oferta"></Oferta>
            </div>
            <div class="odkryj" v-on:click="$parent.current = 'Online'">Odkryj więcej</div>
        </div>
    </div>
</template>

<script>
    import Oferta from './Oferta';
    export default {
        components: {
            Oferta
        },
        data: function () {
            return {
                oferty: [{
                    id: 0,
                    url: 'https://res.cloudinary.com/dj484tw6k/f_auto,q_auto,c_pad,b_white,w_360,h_360/v1507259978/bb/6995.png',
                    nazwa: "Chipsy Lays zielona cebulka",
                    wiecej: "150g",
                    cena: "3.49zł"
                }, {
                    id: 1,
                    url: 'https://www.ezebra.pl/pol_pl_KTC-OLEJ-PALMOWY-CZYSTY-NATURALNY-KOSMETYK-500ML-1237_1.jpg',
                    nazwa: "Olej palmowy",
                    wiecej: "500ml",
                    cena: "10.49zł"
                }, {
                    id: 2,
                    url: 'https://sgfm.elcorteingles.es/SGFM/dctm/MEDIA03/201607/13/00118032900054____2__600x600.jpg',
                    nazwa: "Paella do mikrofali",
                    wiecej: "250g",
                    cena: "6.99zł"
                }, {
                    id: 3,
                    url: 'http://www.maluta.galeo.pro/media/p/74.jpg',
                    nazwa: "Śmietana 18% maluta",
                    wiecej: "400g",
                    cena: "3.99zł"
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
        padding: 10px;
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