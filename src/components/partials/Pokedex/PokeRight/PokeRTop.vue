<script>
export default {
  name: "PokeTop",
};
</script>

<template>
  <div class="poke-container-separator">
    <div class="poke-separator"></div>
    <div class="poke-separator"></div>
    <div class="poke-separator"></div>
    <div class="poke-separator"></div>
    <div class="poke-separator"></div>
    <div class="poke-separator"></div>
  </div>
</template>

<style lang="scss">
.poke-right {
  .poke-container-separator {
    height: 20%;
    position: relative;
  }

  .poke-separator {
    position: absolute;
    width: 100%;
    height: 100%;
    border-right: 2px solid black;
  }

  .poke-separator:nth-child(1) {
    clip-path: polygon(0 0, 0 100%, 100% 100%, 100% 75%, 55% 75%, 25% 0);
    background-color: black;
  }

  .poke-separator:nth-child(2) {
    clip-path: polygon(
      0 1.8%,
      0 100%,
      100% 100%,
      100% 76.5%,
      55% 76.5%,
      25% 1.8%
    );
    background-color: var(--main-background-color);
  }

  .poke-separator:nth-child(3) {
    clip-path: polygon(
      0 11.8%,
      0 100%,
      100% 100%,
      100% 85.4%,
      53% 85.4%,
      23% 11.8%
    );
    background-color: black;
    width: calc(96% - 2px);
    left: 2%;
  }
  .poke-separator:nth-child(4) {
    clip-path: polygon(
      0 13.6%,
      0 100%,
      100% 100%,
      100% 87.4%,
      53% 87.4%,
      23% 13.6%
    );
    background-color: var(--main-shadow-background-color);
    width: calc(96% - 2px);
    border-left: 2px solid black;
    left: 2%;
  }

  .poke-separator:nth-child(5) {
    clip-path: polygon(
      0 19%,
      0 100%,
      100% 100%,
      100% 92.4%,
      52% 92.4%,
      22% 19%
    );
    background-color: black;
    width: calc(96% - 2px);
    left: 2%;
  }
  .poke-separator:nth-child(6) {
    clip-path: polygon(
      0 20.8%,
      0 100%,
      100% 100%,
      100% 93.8%,
      52% 93.8%,
      22% 20.8%
    );
    background-color: var(--main-background-color);
    width: calc(96% - 2px);
    left: 2%;
    border-left: 2px solid black;
    border-right: 2px solid black;
  }
}
</style>