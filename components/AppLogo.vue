<template>
  <div class="VueToNuxtLogo">
    <input type="text" v-model="name">
  </div>
</template>

<style>
.VueToNuxtLogo {
  display: inline-block;
  position: relative;
  overflow: hidden;
  height: 180px;
  width: 245px;
}

.Triangle {
  position: absolute;
  top: 0;
  left: 0;
  width: 0;
  height: 0;
}
</style>

