<template>
  <div class="container">
    <div class="rows">
      <div class="row"></div>
      <div class="row"></div>
      <div class="row"></div>
      <div class="row"></div>
      <div class="row"></div>
    </div>
    <div class="line"></div>
  </div>
</template>

<script>
export default {
  name: "App",
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

.line {
  height: 500px;
  width: 100px;
  border: 1px solid red;
  position: absolute;
  top: 0;
  left: 0;
}
</style>
