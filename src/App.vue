<template>
  <div class="container">
    <div class="rows">
      <div class="row"></div>
      <div class="row"></div>
      <div class="row"></div>
      <div class="row"></div>
      <div class="row"></div>
    </div>
    <div class="elevator-line">
      <div class="elevator" ref="elevatorRef"></div>
    </div>
    <div class="buttons-line">
      <div class="floor floor-5">
        <p>5</p>
        <button data-floor="5" @click="clickHandler">Call Elevator</button>
      </div>
      <div class="floor floor-4">
        <p>4</p>
        <button data-floor="4" @click="clickHandler">Call Elevator</button>
      </div>
      <div class="floor floor-3">
        <p>3</p>
        <button data-floor="3" @click="clickHandler">Call Elevator</button>
      </div>
      <div class="floor floor-2">
        <p>2</p>
        <button data-floor="2" @click="clickHandler">Call Elevator</button>
      </div>
      <div class="floor floor-1">
        <p>1</p>
        <button data-floor="1" @click="clickHandler">Call Elevator</button>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from "@vue/reactivity";
export default {
  name: "App",
  setup() {
    const clickHandler = (e) => {
      const floor = e.target.dataset.floor;
      console.log("i have been clicked", floor);
      console.dir(elevatorRef.value);
      const moveAmount = floor * 100;
      const baseAmount = 500;
      console.log(moveAmount);
      elevatorRef.value.style = `top: ${baseAmount - moveAmount}px`;
    };

    const elevatorRef = ref(null);

    return { clickHandler, elevatorRef };
  },
};
</script>

<style lang="scss">
*,
*::after,
*::before {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.container {
  position: relative;
}

body {
  background: rgb(212, 212, 212);
}

.row {
  border: 1px solid black;
  height: 100px;
}

.elevator-line {
  height: 500px;
  width: 100px;
  border: 1px solid red;
  position: absolute;
  top: 0;
  left: 0;
}

.floor {
  width: 100px;
  height: 100px;
  border: 1px solid green;
  position: absolute;
  top: 0;
  left: 100px;
}

.floor-5 {
  top: 0px;
}
.floor-4 {
  top: 100px;
}
.floor-3 {
  top: 200px;
}
.floor-2 {
  top: 300px;
}
.floor-1 {
  top: 400px;
}

.elevator {
  height: 100px;
  width: 100px;
  background: goldenrod;
  position: absolute;
  bottom: 0;
  left: 0;
}
</style>
