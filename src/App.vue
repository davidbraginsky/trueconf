<template>
  <div class="container">
    <div class="rows">
      <div class="row-wrapper" :key="row" v-for="row in floors">
        <RowElement />
      </div>
    </div>
    <div class="elevator-line">
      <ElevatorElement ref="elevatorElement" />
    </div>
    <div class="buttons-line">
      <FloorElement @callElevator="callHandler" class="floor floor-1" floorNumber="1" />
      <FloorElement @callElevator="callHandler" class="floor floor-2" floorNumber="2" />
      <FloorElement @callElevator="callHandler" class="floor floor-3" floorNumber="3" />
      <FloorElement @callElevator="callHandler" class="floor floor-4" floorNumber="4" />
      <FloorElement @callElevator="callHandler" class="floor floor-5" floorNumber="5" />
    </div>
  </div>
</template>

<script>
import { ref } from "@vue/reactivity";
import RowElement from "./components/RowElement.vue";
import ElevatorElement from "./components/ElevatorElement.vue";
import FloorElement from "./components/FloorElement.vue";
export default {
  name: "App",
  components: {
    RowElement,
    ElevatorElement,
    FloorElement,
  },
  setup() {

    const callHandler = (floor) => {
      console.log(floor);
      const elevator = elevatorElement.value.elevatorRef;
      const moveAmount = floor * 100;
      const baseAmount = 500;
      elevator.style = `top: ${baseAmount - moveAmount}px`;
    };

    const floors = [1, 2, 3, 4, 5];

    const elevatorElement = ref(null);

    return { floors, elevatorElement, callHandler };
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
</style>
