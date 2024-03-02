<script>
export default {
  name: "PokeStats",
  props:{
    pokeStats: Array,
  },
  data() {
    return {
      arrayStatsName: ['HP','Attack','Defens','Sp.Atk','Sp.Def','Speed']
    }
  },
};
</script>

<template>
  <div class="poke-stats border-2-black">
      <div v-for="index in 6" :key="index">
        <p>
          <span>{{ arrayStatsName[index - 1] }}</span>
          <span>{{ pokeStats.length > 0 ? pokeStats[index - 1].base_stat : '???' }}</span>
        </p>
        <div class="stat-bar">
          <div v-if="pokeStats.length > 0" :style="{ width: `${(100 / 255) * pokeStats[index - 1].base_stat}%` }" class="progress"></div>
        </div>
      </div>
    </div>
</template>

<style lang="scss">
// POKE STAT
// -------------------------------------------
.poke-stats {
  height: 29%;
  padding: 4%;
  background-color: var(--display-pokeResults-background-color);
  border-radius: 1.3vw;

  font-size: 1.5vw;
  font-weight: 700;

  display: flex;
  flex-direction: column;
  justify-content: center;
  div {
    display: flex;
    align-items: center;
    gap: 2%;
  }

  p {
    width: 26%;
    margin: 0;
    display: flex;
    justify-content: space-between;

    span:nth-child(2) {
      color: #fff;
      text-shadow: 0 0 8px #000;
    }
  }
}

/* Styles for screens above 1000px */
@media only screen and (min-width: 1000px) {
  .poke-stats {
    font-size: 15px;
  }
}

// STAT BAR
.stat-bar {
  width: 72%;
  height: 50%;
  background-color: #444;
  border-radius: 5px;
  overflow: hidden;
  border: 0.1vw solid black;
}

.progress {
  height: 100%;
  width: 50%;
  background-color: #222;
}
// -------------------------------------------

</style>