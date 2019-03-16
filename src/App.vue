<template>
  <div id="app">
    <div class="top">
      <img src="./assets/real.png" v-on:click="current = 'Glowna'">
      <span style="flex: 1 1 100%"></span>
      <div class="lbtn" v-on:click="current = 'Sklepy'">
        <div>Znajdź sklep!</div>
      </div>
      <div class="lbtn" v-on:click="current = 'Zakupy'">Zakupy on-line</div>
      </div>
    <component
      v-bind:is="currentZakladka"
    ></component>
    <div class="dolek">
      <div class="kitki">
        <div class="kitek">
          Bądź na bieżąco!
          <div class="btnek github" v-on:click="open('https://github.com/pizza61/real')">GitHub</div>
        </div>
        <div class="kitek">
          Zakupy jeszcze łatwiejsze z aplikacją real!
          <div class="btnek apka">Już wkrótce</div>
        </div>
      </div>
      Ta strona nie jest w żaden sposób powiązana z nieistniejącą już siecią sklepów real. Jest to jedynie fanowska wersja strony reala ,-, inspirowana stroną sieci Auchan, która przejęła większość sklepów real.
      <br><br><div>Icons made by <a href="https://www.flaticon.com/authors/smashicons" title="Smashicons">Smashicons</a> from <a href="https://www.flaticon.com/" 			    title="Flaticon">www.flaticon.com</a> is licensed by <a href="http://creativecommons.org/licenses/by/3.0/" 			    title="Creative Commons BY 3.0" target="_blank">CC 3.0 BY</a></div>
      </div>
      
  </div>
</template>

<script>
import Glowna from './components/Glowna';
import Zakupy from "./components/Zakupy";
import Sklepy from "./components/Sklepy";
export default {
  name: 'app',
  components: {
    Glowna,
    Zakupy,
    Sklepy
  },
  data: function() {
    return {
      current: 'Glowna',
      zakladki: ['Glowna', 'Zakupy', 'Sklepy']
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
  font-family: 'Roboto Condensed', sans-serif;
  color: #1b1b1b;
}

//#1d5cb2
.top {
  display: flex;
  position: sticky;
  z-index: 3;
  top: 0;
  background: white;
  box-shadow: 0 1px 2px rgba(0,0,0,0.12);
  align-items: center;
  border: 0.5px solid rgb(230, 231, 235);
  padding: 10px;

  & img {
    height: 50px;
    cursor: pointer;
  }
}

a {
  text-decoration: none;
  color: gold;
}

/*.lbtn {
  display: inline-block;
  background: $realowy;
  border-radius: 1444px;
  //flex-grow: 1;
  color: white;
  font-size: 120%;
  text-align: center;
  cursor: pointer;
  transition: 300ms;
  padding: 20px;
  &:hover {
    background: #143f7a;;
  }
}*/

.lbtn {
  cursor: pointer;
  //margin: 20px;
  margin: 0 5px;
  width: 500px;
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

.semilbtn {
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

.github {
  background: #24292e;

  &:hover {
    background: #171a1d;
  }
}

.apka {
  background: #1d5cb2;

  &:hover {
    background: #143f7a;
  }
}

</style>
