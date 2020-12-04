<template>
  <div :class="'mirror-item ' + this.color">
  </div>
</template>

<script>
export default {
name: "MirrorItem",
  props : {
  name : "",
    color : ""
  },
  data () {
  return {
    name : "",
    color : "m-orange"
  }
  }
}
</script>

<style scoped>
.mirror-item {
  width: 20px;
  height: 40px;
  display: inline-block;
}

.m-orange {
  background-color: darkorange;
}
.m-green {
  background-color: darkolivegreen;
}
</style>
