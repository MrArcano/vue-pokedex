<script>
import Pokedex from "./components/Pokedex.vue";

export default {
  name: "App",
  components: {
    Pokedex,
  },
};
</script>

<template>
  <div class="sky d-flex justify-content-center align-items-center">
    <Pokedex />
  </div>
</template>

<style lang="scss">
:root {
  --sky-lineargradient-firstcolor: #283e51;
  --sky-lineargradient-secondcolor: #0a2342;

  --main-shadow-background-color: #8e062a;
  --main-background-color: #d30a40;
  --pokedex-shade: #d83760;

  --display-container-background-color: #7f7f7f;
  --display-lightgray-background-color: #e3e3e3;

  --display-pokeResults-background-color: #52ae5f;

  --cyan-color: #0decf7;
  --bondiblue-color: #0ebdd2;
  --lightblue-color: #a2f5f8;

  --red-color: #dc041b;
  --darkred-color: #ac0011;
  --darkyellow-color: #a28c11;
  --yellow-color: #f3dd51;
  --darkgreen-color: #6ea838;
  --green-color: #2bff00;
}

.sky {
  height: 100vh;
  width: 100%;
  background: url("http://www.script-tutorials.com/demos/360/images/stars.png") repeat top center,
    linear-gradient(
      to top,
      var(--sky-lineargradient-firstcolor),
      var(--sky-lineargradient-secondcolor)
    );
}
</style>
