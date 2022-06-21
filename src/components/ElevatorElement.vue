<template>
  <div class="elevator" ref="elevatorRef"></div>
</template>

<script setup>
import { ref, defineExpose } from "vue";

const elevatorRef = ref(null);

defineExpose({
  elevatorRef,
});
</script>

<style>
.elevator {
  height: 100px;
  width: 100px;
  background: goldenrod;
  position: absolute;
  bottom: 0;
  left: 0;
}
</style>
