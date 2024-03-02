<script>
export default {
  name: "PokeTop",
  props: {
    stateBtn: String,
  }
};
</script>

<template>
  <div class="poke-top">
    <div class="poke-container-separator">
      <div class="poke-separator"></div>
      <div class="poke-separator">
        <div class="separator-mark"></div>
        <div class="separator-mark"></div>
        <div class="separator-mark"></div>
        <div class="separator-mark"></div>
        <div class="separator-mark"></div>
        <div class="separator-mark"></div>
        <div class="separator-mark"></div>
      </div>
      <div class="poke-separator"></div>
      <div class="poke-separator"></div>
    </div>

    <div class="poke-button">
      <!-- Button white/cyan -->
      <div class="big-btn-white-cyan border-2-black circle">
        <div class="cyan-container border-2-black circle">
          <div class="bondiblue-container circle"></div>
          <div class="small-cyan-container cyan-container circle">
            <div class="lightblue-container circle"></div>
          </div>
        </div>
      </div>

      <!-- 3 btn colored -->
      <!-- RED -->
      <div class="coloredBtn red-container border-2-black circle">
        <div class="lightred-container circle light-circle"></div>
        <div class="darkred-container circle dark-circle"></div>
      </div>
      <!-- YELLOW -->
      <div class="coloredBtn yellow-container border-2-black circle">
        <div class="lightyellow-container circle light-circle"></div>
        <div class="darkyellow-container circle dark-circle"></div>
      </div>
      <!-- GREEN -->
      <div class="coloredBtn green-container border-2-black circle">
        <div class="lightgreen-container circle light-circle"></div>
        <div class="darkgreen-container circle dark-circle"></div>
      </div>
    </div>

    <div v-if="stateBtn" class="poke-save">
      <button @click="$emit('editPokeList')" class="btn-csm">{{ stateBtn }}</button>
    </div>
  </div>
</template>

<style lang="scss">
.poke-top {
  height: 20%;
  position: relative;
}

// POKE BUTTON TOP
// -------------------------------------------
.poke-button {
  height: 100%;
  display: flex;
  align-items: flex-start;
  gap: 3%;
  width: 86.2%;
  border-right: 2px solid black;
}
.poke-left{
  // POKE SEPARATOR
  .poke-separator {
    position: absolute;
    width: 100%;
    height: 100%;
    border-radius: 1.8vw 0.8vw 0vw 0vw;
  }
  
  .poke-separator:nth-child(1) {
    background-color: black;
    clip-path: polygon(0% 0%, 0% 100%, 40% 100%, 65% 32%, 100% 32%, 100% 0);
  }
  .poke-separator:nth-child(2) {
    background-color: var(--main-shadow-background-color);
    clip-path: polygon(
      0% 0%,
      0% 98.5%,
      39.8% 98.5%,
      64.8% 30.5%,
      96% 30.5%,
      100% 30%,
      100% 0%
    );
  }
  .poke-separator:nth-child(3) {
    background-color: black;
    clip-path: polygon(
      0% 0%,
      0% 89%,
      38.2% 89%,
      63.2% 22.5%,
      96% 22.5%,
      100% 30%,
      100% 0%
    );
  }
  .poke-separator:nth-child(4) {
    background-color: var(--main-background-color);
    clip-path: polygon(
      0% 0%,
      0% 87.5%,
      38% 87.5%,
      63% 21%,
      96% 21%,
      100% 30%,
      100% 0%
    );
  }
  
  .separator-mark {
    background-color: black;
    width: 2px;
    height: 20%;
    bottom: 0;
    left: 25%;
    position: absolute;
    transform: rotate(16deg);
  }
  .separator-mark:nth-child(2) {
    left: 26.5%;
  }
  .separator-mark:nth-child(3) {
    left: 28%;
  }
  .separator-mark:nth-child(4) {
    left: 29.5%;
  }
  .separator-mark:nth-child(5) {
    left: 31%;
  }
  .separator-mark:nth-child(6) {
    left: 32.5%;
  }
  .separator-mark:nth-child(7) {
    left: 34%;
  }
}

// BIG BUTTON
.big-btn-white-cyan {
  background-color: #fff;
  width: 28%;
  aspect-ratio: 1/1;
  top: 4%;
  left: 1.5%;
  position: relative;
}

.cyan-container {
  background-color: var(--cyan-color);
  height: 83%;
  width: 83%;
  position: absolute;
  top: 5%;
  right: 5%;
}

.cyan-container .bondiblue-container {
  background-color: var(--bondiblue-color);
  height: 90%;
  width: 94%;
  position: absolute;
  right: 0;
  bottom: 0;
}

.cyan-container .small-cyan-container {
  height: 50%;
  width: 55%;
  right: 25%;
}

.small-cyan-container .lightblue-container {
  background-color: var(--lightblue-color);
  height: 50%;
  width: 43%;
  position: absolute;
  top: 10%;
  left: 25%;
}

// SMALL BUTTON
// -------------------------------------------

.coloredBtn {
  width: 8%;
  aspect-ratio: 1/1;
  position: relative;
  top: 6%;
}

.light-circle {
  height: 50%;
  width: 55%;
  z-index: 10;
  position: absolute;
  top: 10%;
  right: 30%;
}

.dark-circle {
  height: 80%;
  width: 90%;
  position: absolute;
  right: 0;
  bottom: 0;
}
// RED
.coloredBtn.red-container {
  background-color: var(--red-color);
}

.red-container .lightred-container {
  background-color: var(--red-color);
}

.red-container .darkred-container {
  background-color: var(--darkred-color);
}

// YELLOW
.coloredBtn.yellow-container {
  background-color: var(--yellow-color);
}

.yellow-container .lightyellow-container {
  background-color: var(--yellow-color);
}

.yellow-container .darkyellow-container {
  background-color: var(--darkyellow-color);
}

// GREEN
.coloredBtn.green-container {
  background-color: var(--green-color);
}

.green-container .lightgreen-container {
  background-color: var(--green-color);
}

.green-container .darkgreen-container {
  background-color: var(--darkgreen-color);
}
// -------------------------------------------

.poke-save{
  position: absolute;
  bottom: 2%;
  right: 16%;
  .btn-csm{
    width: 100%;
    padding: 0.1vw 2vw;
  }
}
</style>