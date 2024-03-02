<script>
export default {
  name: "PokeBox",
  methods: {
    sendStartSearch(event){
      const testoElemento = event.currentTarget.querySelector('span').textContent;
      this.$emit('startSearch', testoElemento);
    }
  },
};
</script>

<template>
  <div class="poke-bottom">
    <div class="poke-container border-2-black">
      <div class="poke-saved-list border-2-black">
        <p class="text-center">Saved Pokemon</p>
        <ul>
          <li @click="sendStartSearch">
            <img src="/pokeball.png" alt="li-poke" /><span>bulbasaur</span>
          </li>
        </ul>
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
    p {
      margin-bottom: 2%;
    }

    ul {
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
        }
      }
    }
  }

  @media only screen and (min-width: 1000px) {
    .poke-saved-list {
      font-size: 15px;
    }
  }
}
</style>