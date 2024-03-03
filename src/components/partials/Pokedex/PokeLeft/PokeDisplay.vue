<script>
export default {
  name: "PokeDisplay",
  props:{
    pokeData: Object,
  },
  methods: {
    changePoke(direction){
      let idSearch = 1;
      if(this.pokeData.name !== 'Not Found!'){
        if(direction === 'next'){
          idSearch = this.pokeData.id + 1;
        }
        if(direction === 'prev'){
          idSearch = this.pokeData.id - 1;
        }
      }

      if(idSearch === 1026){
        idSearch = 10001;
      }

      if(idSearch > 0){
        this.$emit('startSearch',idSearch);
      }
    },

    ImageError(event){
      event.target.src = '/question-mark.png';
    }
  },
  computed: {
    getImage(){
      if(Object.keys(this.pokeData.sprites).length !== 0){
        return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/${this.pokeData.id}.png`
      }
      return '/question-mark.png'
    }
  },
};
</script>

<template>
  <div class="poke-display-border path-display">
      <div class="poke-display-shadow path-display">
        <div class="poke-display-border path-display">
          <div class="poke-display path-display">
            <div class="poke-display-top">
              <button @click="changePoke('prev')" class="btn-csm">&laquo;</button>
              <div class="poke-screw">
                <div class="screw border-2-black"></div>
                <div class="screw border-2-black"></div>
              </div>
              <button @click="changePoke('next')" class="btn-csm">&raquo;</button>
            </div>
            <div class="poke-bg-image border-2-black">
              <div class="poke-image">
                <img :title="pokeData.name"
                  :src="getImage" @error="ImageError" alt="Pokémon"
                />
              </div>
            </div>
            <h1 class="poke-data">
              <span class="poke-number">{{ pokeData.id }}</span>
              <span> - </span>
              <span class="poke-name" :title="pokeData.name" >{{ pokeData.name }}</span>
            </h1>
          </div>
        </div>
      </div>
    </div>
</template>

<style lang="scss">

.path-display {
  clip-path: polygon(0 0, 100% 0, 100% 100%, 17% 100%, 0 80%);
}

.poke-display-border {
  height: 100%;
  background-color: black;
  border-radius: 1.2vw 1vw 1.3vw 0;
  padding: 0% 0.1% 0.6% 0.6%;
}

.poke-container > .poke-display-border {
  height: 56%;
  border-radius: 1vw 1vw 2.2vw 0;
  padding: 0.6%;
}

.poke-display-shadow {
  height: 100%;
  background-color: var(--display-container-background-color);
  border-radius: 1vw 1vw 2vw 0;
  padding: 0% 0% 1.3% 1.3%;
}

.poke-display {
  height: 100%;
  background-color: var(--display-lightgray-background-color);
  border-radius: 1.3vw 1vw 1.4vw 0;

  position: relative;
}
// -------------------------------------------
.poke-display-top{
  display: flex;
  justify-content: center;
  align-items: center;

  height: 14%;
  width: 80%;
  margin: 0 auto;

  button{
    padding: 0 0.4vw;
    line-height: 100%;
    box-shadow: none;
  }
}

.poke-screw {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 80%;
  gap: 5%;
}

.screw {
  width: 5%;
  aspect-ratio: 1/1;
  background-color: var(--main-background-color);
  border-radius: 50%;
}
// -------------------------------------------

.poke-bg-image {
  background-image: url(https://guilhermescr.github.io/modern-pokedex/with-javascript/assets/images/pokemonScenario_display_background.jpg);
  background-position: center;
  background-size: cover;
  width: 80%;
  aspect-ratio: 235/153;
  margin: 0 auto;
  border-radius: 0.6vw;

  display: flex;
  justify-content: center;
  align-items: center;
}

.poke-image {
  width: 55%;
  img {
    width: 100%;
  }
}
// -------------------------------------------

.poke-data {
  margin: 2% 10%;
  text-align: right;
  position: absolute;
  bottom: 0;
  right: 0;
  font-size: 2.6vw;
  font-weight: 600;
  color: #aaa;
  width: 75%;

  white-space: nowrap; 
  overflow: hidden;
  text-overflow: ellipsis; 
}

.poke-name {
  color: #3a444d;
  text-transform: capitalize;
}

/* Styles for screens above 1000px */
@media only screen and (min-width: 1000px) {
  .poke-data {
    font-size: 26px;
  }
}
// -------------------------------------------

</style>