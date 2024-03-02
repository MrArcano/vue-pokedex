<script>
export default {
  name: "PokeSearch",
  data() {
    return {
      value: '',
    }
  },
  methods: {
    sendStartSearch(){
      if(this.value !== ''){
        this.$emit('startSearch',this.value);
        this.value = '';
      }
    }
  },
};
</script>

<template>
  <div class="poke-search">
      <input @keypress.enter="sendStartSearch" v-model.trim="value" type="search" id="inputPokemonName" placeholder="Name / ID" spellcheck="false"/>
      <button @click="sendStartSearch" class="btn-csm">
        <i class="fa-solid fa-magnifying-glass"></i>
      </button>
    </div>
</template>

<style lang="scss">
// INPUT SEARCH
// -------------------------------------------
.poke-search {
  margin-top: 2%;
  margin-bottom: 4%;
  text-align: right;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 3%;
  input {
    background-color: var(--display-lightgray-background-color);
    box-shadow: -3px 4px 0 #888, -5px 7px 0 #333;
    border: 2px solid #333;
    border-radius: 5px;
    color: #3a444d;
    outline-style: none;
    padding: 4%;
    width: 80%;

    font-weight: 600;
    font-size: 1.6vw;
  }
}

/* Styles for screens above 1000px */
@media only screen and (min-width: 1000px) {
  .poke-search {
    input {
      font-size: 16px;
    }
  }
}
// -------------------------------------------

// -------------------------------------------
.btn-csm {
  width: 15.5%;
  aspect-ratio: 1/1;

  border: 2px solid #000;
  border-radius: 5px;
  font-size: clamp(8px, 5vw, 1rem);
  font-weight: 600;
  color: white;
  background-color: #444;
  box-shadow: -2px 3px 0 #222, -4px 6px 0 #000;
  font-size: 1.6vw;
}

.btn-csm:active {
  transform: scale(0.95);
}

/* Styles for screens above 1000px */
@media only screen and (min-width: 1000px) {
  .btn-csm {
    font-size: 16px;
  }
}
// -------------------------------------------
</style>