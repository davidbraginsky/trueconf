<template>
  <div>
    <p>{{ props.floorNumber }}</p>
    <button :data-floor="props.floorNumber" @click="$emit('callElevator', props.floorNumber)">Call Elevator</button>
  </div>
</template>

<script>
export default {
  name: "FloorElement",
  props: ["floorNumber"],
  setup(props) {
    return { props };
  },
};
</script>

<style></style>
