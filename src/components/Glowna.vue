<template>
<div>
    <div class="prezentacja">
        <div class="obrazek">
            <img height=450 src="https://www.real.de/fileadmin/realde/subpages/eigenmarken/Images/tip_taeglicher_bedarf.png">
        </div>
        <div class="opis">
            <h1>Produkty marki tip</h1>
            <h3>Najwyższa jakość w najniższej cenie. Tylko w sklepach real ,-</h3>
            <img src="https://www.testberichte.de/imgs/p_imgs/Real+++Tip+Pizza+Edelsalami-936003.jpg">
        </div>
    </div>
    <div class="prezentacja">
        <div class="opis">
            <h1>Kup starter Plusha w realu ,-</h1>
            <h3>Zarejestruj u nas numer, a otrzymasz 20 GB gratis</h3>
        </div>
        <div class="obrazek">
            <img src="http://dzieciowo.pl/wp-content/uploads/2014/10/plush.jpg">
        </div>
    </div>
    <div class="lista">
        <img class="lista-maly" src="../assets/real.png">
        <span class="lista-tytul">Oferty reala ,-</span>
        <!--<div class="oferta" v-bind:key="oferta.id" v-for="oferta in oferty">
            <span>{{ oferta.nazwa }}</span>
        </div>-->
        <div class="oferty">
        <Oferta v-bind:key="oferta.id" v-for="oferta in oferty" v-bind:data="oferta">

        </Oferta>
        </div>
        <div class="odkryj">A to wszystko w twoim sklepie real!</div>
    </div>
</div>
</template>

<script>
import Oferta from './Oferta';
export default {
    components: {
        Oferta
    },
    data: function() {
        return {
            oferty: [{
                id: 0,
                url: 'https://res.cloudinary.com/dj484tw6k/f_auto,q_auto,c_pad,b_white,w_360,h_360/v1507259978/bb/6995.png',
                nazwa: "Chipsy Lays zielona cebulka",
                wiecej: "150g",
                cena: "3.50zł"
            },{
                id: 1,
                url: 'https://www.ezebra.pl/pol_pl_KTC-OLEJ-PALMOWY-CZYSTY-NATURALNY-KOSMETYK-500ML-1237_1.jpg',
                nazwa: "Olej palmowy",
                wiecej: "500ml",
                cena: "10.50zł"
            },{
                id: 2,
                url: 'https://sgfm.elcorteingles.es/SGFM/dctm/MEDIA03/201607/13/00118032900054____2__600x600.jpg',
                nazwa: "Paella do mikrofali",
                wiecej: "250g",
                cena: "6.99zł"
            },{
                id: 3,
                url : 'http://www.maluta.galeo.pro/media/p/74.jpg',
                nazwa: "Śmietana 18% maluta",
                wiecej: "400g",
                cena: "3.99zł"
            }]
        }
    },
  methods: {
    open: function(lnk) {
      window.location.href = lnk
    }
  }
}
</script>

<style lang="scss">
    .prezentacja {
        display: flex;
    }
    .obrazek {
        height: 100%;
    }
    .opis {
        margin: 20px;
        flex-grow: 1;
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
    }
    .odkryj {
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
</style>
