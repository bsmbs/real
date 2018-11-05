<template>
  <div id="app">
    <div class="top">
      <img src="./assets/real.png" v-on:click="current = 'Glowna'">
    </div>
    <div class="btns">
      <div class="lbtn" v-on:click="current = 'Sklepy'">
        <div>Znajdź sklep!</div>
      </div>
      <div class="lbtn" v-on:click="current = 'Online'">Zakupy on-line</div>
    </div>
    <component
      v-bind:is="currentZakladka"
    ></component>
    <div class="dolek">
      <div class="kitki">
        <div class="kitek">
          Bądź na bieżąco!
          <div class="btnek" style="background: #24292e;" v-on:click="open('https://github.com/pizza61/real')">GitHub</div>
        </div>
        <div class="kitek">
          Zakupy jeszcze łatwiejsze z aplikacją real!
          <div class="btnek" style="background: #1d5cb2;">Już wkrótce</div>
        </div>
      </div>
      Ta strona nie jest w żaden sposób powiązana z nieistniejącą już siecią sklepów real. Jest to jedynie fanowska wersja strony reala ,-, inspirowana stroną sieci Auchan, która przejęła większość sklepów real.</div>
  </div>
</template>

<script>
import Glowna from './components/Glowna';
import Online from "./components/Online";
import Sklepy from "./components/Sklepy";
export default {
  name: 'app',
  components: {
    Glowna,
    Online,
    Sklepy
  },
  data: function() {
    return {
      current: 'Glowna',
      zakladki: ['Glowna', 'Online', 'Sklepy']
    }
  },
  computed: {
    currentZakladka: function() {
      return this.current.toLowerCase()
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

$realowy: #1d5cb2;

body {
  margin: 0;
  font-family: 'Ubuntu', sans-serif;
} //#1d5cb2
.top {

  border: 0.5px solid rgb(230, 231, 235);
  padding: 10px;
  & img {
    height: 50px;
    cursor: pointer;
  }
}

.btns {  
  background: white;
  border-bottom: 0.5px solid rgb(230, 231, 235);
  position: sticky;
  top: 0;
  display: flex;
}

.lbtn {
  background: $realowy;
  border-radius: 5px;
  flex-grow: 1;
  color: white;
  margin: 10px 5px;
  font-size: 120%;
  text-align: center;
  cursor: pointer;
  transition: 100ms;
  padding: 20px;
  &:hover {
    filter: grayscale(0.8)
  }
}
.dolek {
  background: #333333;
  font-weight: bold;
  font-size: 90%;
  color: white;
  padding: 20px;
}
.kitki {
  display: flex;
  margin: 20px;
}
.kitek {
  font-size: 120%;
  flex-grow: 1;
  text-align: center;
  &:first {
    border-right: 1px solid white;
  }
}
.btnek {
      margin: 20px;
        text-align: center;
        display: inline-block;
        border-bottom-left-radius: 128487px;
        border-top-left-radius: 128487px;
        border-top-right-radius: 128487px;
        border-bottom-right-radius: 128487px;
        color: white;
        padding: 18px 32px;
        font-weight: bold;
        font-size: 90%;
        transition: 300ms;
        cursor: pointer;
        user-select: none;
}
</style>
