<template>
  <div class="heat-item">
    <span class="heat-text">{{heatLevel === 0 ? '&mdash;' : heatLevel}}</span>
  </div>
</template>

<script>
export default {
name: "HeatItem",
  props : {
  heatName : String,
    heatLevel : Number
  },
}
</script>

<style scoped>
.heat-item {
  display: inline-block;
  width: 40px;
  height: 50px;
}
.heat-text {
  font-weight: 300;
  font-size: 24px;
  color: #35495e;
  letter-spacing: 1px;
}
</style>
