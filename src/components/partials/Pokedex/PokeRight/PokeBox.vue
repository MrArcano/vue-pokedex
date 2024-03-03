<script>
export default {
  name: "PokeBox",
  props:{
    pokeList: Array,
  },
  data() {
    return {
      currentIndex: 0,
      itemsPerPage: 20,
    }
  },
  methods: {
    sendStartSearch(name){
      if(name){
        this.$emit('startSearch', name);
      }
    },

    changeView(direction){
      if(direction === 'next'){
        if (this.currentIndex + this.itemsPerPage < this.pokeList.length) {
          this.currentIndex += this.itemsPerPage;
        }
      }

      if(direction === 'prev'){
        if (this.currentIndex >= this.itemsPerPage) {
          this.currentIndex -= this.itemsPerPage;
        }
      }
      
    }
  },
  computed: {
    displayedItems() {
      const start = this.currentIndex;
      const end = start + this.itemsPerPage;
      this.pokeList.sort((a, b) => a.id - b.id);
      const newArray = this.pokeList.slice(start, end);
      return newArray;
    }
  },
};
</script>

<template>
  <div class="poke-bottom">
    <div class="poke-container border-2-black">
      <div class="poke-saved-list border-2-black">
        <div class="d-flex justify-content-around  align-items-center">
          <button @click="changeView('prev')" class="btn-csm" :class="{ 'disabled': currentIndex === 0 }">Prev</button>
          <p class="text-center">Saved Pokemon</p>
          <button @click="changeView('next')" class="btn-csm" :class="{ 'disabled': currentIndex + itemsPerPage >= pokeList.length }">Next</button>
        </div>

        <div class="box-container">
          <div v-for="index in 20" :key="index" @click="sendStartSearch(displayedItems[index-1] ? displayedItems[index-1].name : '')" class="box-item">
            <img class="img-fluid opacity-25" src="/pokeball.png" alt="li-poke" />
            <img v-if="index <= displayedItems.length" class="img-fluid" :src="`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/${displayedItems[index-1].id}.png`" :alt="displayedItems[index-1].name">
          </div>
        </div>

      </div>
    </div>
  </div>
</template>

<style lang="scss">
.poke-right {
  .poke-bottom {
    background-color: var(--main-background-color);
    height: 80%;
    border-right: 2px solid black;
    border-bottom: 2px solid black;
    border-bottom-right-radius: 2vw;
    padding: 0% 2% 2% 2%;
    margin-top: -1px;
    position: relative;
  }

  .poke-container {
    border-top: none;
    border-bottom-right-radius: 2vw;
    height: 100%;
    padding: 4%;
  }

  .poke-saved-list {
    background-color: var(--display-pokeResults-background-color);
    border-radius: 1.3vw;
    height: 100%;
    font-size: 1.5vw;
    font-weight: 700;
    padding: 4%;

    & > div:nth-child(1){
      margin-bottom: 4%;
    }


    p {
      margin: 0;
    }

    ul {
      height: 95%;
      overflow: auto;
      margin-bottom: 2%;
      padding-left: 0;
      list-style: none;

      li {
        display: flex;
        align-items: center;
        gap: 1%;
        img {
          width: 5%;
        }
        span {
          margin-bottom: -1%;
          text-transform: capitalize;
        }

        &:hover{
          color: white;
          text-shadow: 0 0 8px #000;
          cursor: pointer;
          img{
            filter: invert(1);
          }
        }
      }
    }
  }

  @media only screen and (min-width: 1000px) {
    .poke-saved-list {
      font-size: 15px;
    }
  }

  .box-container{
    display: flex;
    flex-wrap: wrap;
  }

  .box-item{
    width: calc(92% / 4);
    aspect-ratio: 1/1;

    background-color: rgba(0, 0, 0, 0.2);
    border-radius: 0.5vw;
    margin: 1%;
    padding: 1%;

    position: relative;

    &:hover{
      cursor: pointer;
      scale: 0.95;
    }


    img:nth-child(2){
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%,-50%);
      width: 70%;
    }
  }

  

}
</style>