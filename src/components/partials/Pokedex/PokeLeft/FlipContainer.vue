<script>
export default {
  name: "FlipContainer",
};
</script>

<template>
  <div class="flip-container border-2-black">
    <div class="flip-shade"></div>
    <div class="flip-divider">
      <div class="flip-mark"></div>
      <div class="flip-mark"></div>
    </div>
    <div class="flip-divider">
      <div class="flip-mark"></div>
      <div class="flip-mark"></div>
    </div>
    <div class="flip-bottom border-2-black"></div>
  </div>
</template>

<style lang="scss">
// FLIP CONTAINER
// -------------------------------------------
.flip-container {
  position: absolute;
  right: 0;
  bottom: 0;
  height: 96%;
  width: 12%;
  padding-left: 10px;

  background-color: var(--main-background-color);
  border-radius: 32px 32px 16px 16px / 16px 16px 16px 16px;
  margin-right: -2px; //for delete border right
}

.flip-bottom {
  background-color: var(--main-shadow-background-color);
  margin: 0 -2px;
  border-radius: 50%;
  width: calc(100% + 4px);
  height: 5.5%;
  position: absolute;
  bottom: -1%;
  left: 0;
  z-index: 2;
}

.flip-divider {
  position: absolute;
  margin: 0 -2px;
  width: calc(100% + 4px);
  height: 2%;
  left: 0;
  top: 10%;
}

.flip-divider:nth-child(2) {
  top: 85%; /* Distanza top per il secondo flip-divider */
}

.flip-divider::before,
.flip-divider::after {
  content: "";
  display: block;
  border: 2px solid black;
  width: 100%;
  height: 100%;
  border-radius: 32px 32px 0px 0px / 16px 16px 0px 0px;
  border-bottom: none;
}

.flip-divider .flip-mark {
  background-color: #000;
  height: 100%;
  width: 2px;
  position: absolute;
  top: 8%;
  right: 24%;
}

.flip-divider .flip-mark:nth-child(2) {
  top: 32%;
  right: 12%; /* Distanza top per il secondo flip-divider */
}

.flip-shade {
  background-color: rgba(255, 255, 255, 0.16);
  border-radius: 32px 32px 0px 0px / 16px 16px 0px 0px;
  height: 98%;
  width: 8%;
  position: absolute;
  top: 0.4%;
  left: 16%;
  z-index: 1;
}

.flip-shade::before,
.flip-shade::after {
  content: "";
  background-color: rgba(255, 255, 255, 0.16);
  border-radius: 32px 32px 0px 0px / 16px 16px 0px 0px;
  height: 100%;
  width: 20%;
  position: absolute;
  z-index: 1;
}

.flip-shade::before {
  top: 0.3%;
  left: -70%;
}

.flip-shade::after {
  top: -0.2%;
  right: -60%;
}
// -------------------------------------------
</style>