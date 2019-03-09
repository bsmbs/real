<template>
<div>
    <div class="mapki">
        <div id="map"></div>
        <div class="obokmapki">
            
            <div class="ccc" v-if="wybor">
                <h2>real {{ sklepy[choicc].title }}</h2>
                <p>Godziny otwarcia</p>
                <p><b>Poniedziałek - piątek</b> {{ wybor.otwarcia.pnpt }}</p>
                <p><b>Sobota</b> {{ wybor.otwarcia.sob }}</p>    
                <p><b>Niedziela (handlowa)</b> {{ wybor.otwarcia.nd }}</p>    
            </div>
            <p v-else>Wybierz sklep z mapki</p>
        </div>
    </div>
    </div>
</template>

<script>

export default {
    beforeMount: function() {
        window.scrollTo({top: 0})
    },
    data: function() {
        return {
            sklepy: [
                {
                    pozycja: {lat: 53.837194, lng: 22.972178},
                    title: "Augustów",
                    otwarcia: {
                        pnpt: "8:00 - 23:00",
                        sob: "9:00 - 21:00",
                        nd: "10:00 - 20:00"
                    }
                },
                {
                    pozycja: {
                        lat: 54.121545, 
                        lng: 17.981222
                    },
                    title: "Kościerzyna",
                    otwarcia: {
                        pnpt: "7:00 - 21:00",
                        sob: "8:00 - 20:00",
                        nd: "8:00 - 20:00"
                    }
                }
            ],
            choicc: 0,
        }
    },
    computed: {
        wybor() {
            return this.sklepy[this.choicc];
        }
    },
    mounted: function() {
        let icon = L.icon({
            iconUrl: 'https://s.mamotoja.pl/media/cache/450x450/media/shop/201107/695_01_2740.jpg',
            iconSize: [32, 32],
            iconAnchor: [16, 16]
        })
        let map = L.map('map').setView([51.979827, 19.568039], 6);
 
        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
            attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
        }).addTo(map);

        let c = this;
        this.sklepy.forEach(function(sklep, i) {
            L.marker([sklep.pozycja.lat, sklep.pozycja.lng], { icon })
            .addTo(map)
            .on("click", function() {
                c.choicc = i;
                console.log(this.choicc)
                map.setView([sklep.pozycja.lat, sklep.pozycja.lng], map.getZoom()+4)
            })
        })
    
    }
}
</script>

<style lang="scss">
.ccc span {
    display: block;
}
.mapki {
    position: relative;
    //display: flex;
}
.mapki > * {
    //flex-grow: 1;
}
.obokmapki {
    box-shadow: 1px 2px 8px rgba(0,0,0,0.24);
    right: 0;
    top: 0;
    position: absolute;
    background: #1d5cb2;
    border-radius: 8px;
    padding: 20px;
    margin: 20px;
    color: white;
}
#map {
    z-index: 0;
    flex-basis: 50%;
    //width: 800px;
    //max-width: 100%;
    height: 600px;
    //height: 600px;
    margin: 0 auto;
    background: gray;
}
</style>
