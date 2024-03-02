<script>
// LEFT
import PokeLTop from "./partials/Pokedex/PokeLeft/PokeLTop.vue";
import FlipContainer from "./partials/Pokedex/PokeLeft/FlipContainer.vue";
import PokeDisplay from "./partials/Pokedex/PokeLeft/PokeDisplay.vue";
import PokeSearch from "./partials/Pokedex/PokeLeft/PokeSearch.vue";
import PokeStats from "./partials/Pokedex/PokeLeft/PokeStats.vue";

// RIGHT
import PokeRTop from "./partials/Pokedex/PokeRight/PokeRTop.vue";
import PokeBox from "./partials/Pokedex/PokeRight/PokeBox.vue";

// AXIOS
import axios from "axios";

export default {
  name: "Pokedex",
  components: {
    // LEFT
    PokeLTop,
    FlipContainer,
    PokeDisplay,
    PokeSearch,
    PokeStats,
    // RIGHT
    PokeRTop,
    PokeBox,
  },
  data() {
    return {
      pokeName: "",
      pokeId: "",
      pokeSprites: {},
      pokeStats: [],
      pokeList: [],
      stateBtn: "",
    };
  },
  methods: {
    getPokemon(value) {
      axios
        .get(`https://pokeapi.co/api/v2/pokemon/${value}`)
        .then((response) => {
          // handle success
          console.log(response.data);

          this.pokeId = response.data.id;
          this.pokeName = response.data.name;
          this.pokeSprites = response.data.sprites;
          this.pokeStats = response.data.stats;
          this.checkList();
        })
        .catch((error) => {
          // handle error
          console.log(error);
          this.pokeId = "?";
          this.pokeName = "Not Found!";
          this.pokeSprites = {};
          this.pokeStats = [];
        });
    },

    checkList(){
      if(this.pokeList.includes(this.pokeName)){
        this.stateBtn = 'Delete';
        return true;
      }else{
        this.stateBtn = 'Save';
        return false;
      }
    },

    editList(){
      if(this.checkList()){
        this.pokeList = this.pokeList.filter(item => item !== this.pokeName);
      }else{
        this.pokeList.push(this.pokeName);
      }
      localStorage.setItem('pokeList', this.pokeList);
      this.checkList();
    }
  },
  mounted() {
    this.getPokemon(1);
    this.pokeList = localStorage.getItem('pokeList').split(',') ?? [];
  },
};
</script>

<template>
  <div class="poke-base">
    <!-- LEFT -->
    <div class="poke-left-shadow border-2-black">
      <div class="poke-left border-2-black">
        <PokeLTop @editPokeList="editList" :stateBtn="stateBtn" />

        <div class="poke-container border-2-black">
          <PokeDisplay
            :pokeData="{ id: pokeId, name: pokeName, sprites: pokeSprites }"
          />
          <PokeSearch @startSearch="getPokemon" />
          <PokeStats :pokeStats="pokeStats" />
        </div>

        <FlipContainer />
      </div>
    </div>

    <!-- RIGHT -->
    <div class="poke-right">
      <PokeRTop />
      <PokeBox @startSearch="getPokemon" :pokeList="pokeList" />
    </div>
  </div>
</template>

<style lang="scss">
// ----------------------------------
// -------------- BASE --------------
// ----------------------------------
.poke-base {
  max-width: 900px;
  /* height: 570px; */
  width: 90%;
  aspect-ratio: 785/640;
  display: flex;
}

// ----------------------------------
// -------------- LEFT --------------
// ----------------------------------

.poke-left-shadow {
  background-color: var(--main-shadow-background-color);
  width: 54%;
  // box-shadow: -4px 0px 8px 4px #888888;
  border-radius: 2.1vw 3.2vw 1.4vw 3vw;
  position: relative;
}

.poke-left {
  height: 98%;
  margin-left: 3%;
  margin-right: -2px; //for delete border right
  margin-top: -2px;
  background-color: var(--main-background-color);
  border-radius: 2vw 0.8vw 1.2vw 2.4vw;
}

// -----------------------------------
// ------------ CONTAINER ------------
// -----------------------------------

.poke-left .poke-container {
  border-bottom-left-radius: 2vw;
  border-top: 0;
  height: 79%;
  margin: 0% 13.8% 1% 1.6%;
  padding: 2%;
}

// -----------------------------------
// -------------- RIGHT --------------
// -----------------------------------

.poke-right {
  width: 46%;
  height: 91.5%;
  margin-top: 5%;
}
</style>