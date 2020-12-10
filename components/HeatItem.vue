<template>
  <div class="heat-item">
    <span class="heat-text">{{heatLevel}}</span>
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
  width: 15px;
}
.heat-text {

}
</style>
