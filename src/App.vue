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
      <div class="floor-wrapper" :key="item" v-for="item in floors">
        <FloorElement @callElevator="callHandler" class="floor" :floorNumber="item" />
      </div>
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
    let currentFloor = ref(1);

    const callHandler = (floor) => {
      const elevator = elevatorElement.value.elevatorRef;
      const floorDistance = Math.abs(floor - currentFloor.value);
      const moveAmount = floor * 100;
      const baseAmount = 100;
      const totalAmount = moveAmount - baseAmount;
      elevator.setAttribute("style", `transform: translateY(-${totalAmount}px); transition-duration: ${floorDistance}s; animation-delay: ${floorDistance}s`);
      currentFloor.value = floor;
      if (elevator.classList.contains("isIdle")) {
        elevator.classList.remove("isIdle");
        void elevator.offsetWidth;
        elevator.classList.add("isIdle");
      } else {
        elevator.classList.add("isIdle");
      }
    };

    let isIdle = ref(false);

    const floors = [5, 4, 3, 2, 1];

    const elevatorElement = ref(null);

    return { floors, elevatorElement, callHandler, isIdle, currentFloor };
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

.isIdle {
  animation-name: blink;
  animation-duration: 1s;
  animation-iteration-count: 3;
  animation-fill-mode: both;
}

.isMoving {
  animation-name: moveOneFloor;
  animation-duration: 1s;
  animation-fill-mode: forwards;
}

.floor {
  width: 100px;
  height: 100px;
  border: 1px solid green;
  top: 0;
  left: 100px;
}

.buttons-line {
  position: absolute;
  top: 0;
  left: 100px;
}

@keyframes blink {
  0% {
    opacity: 1;
  }

  50% {
    opacity: 0;
  }

  100% {
    opacity: 1;
  }
}
</style>
