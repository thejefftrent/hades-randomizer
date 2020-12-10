<template>
  <div :class="'mirror-item ' + this.color">
    <p class="mirror-item-text">{{ this.itemName }}</p>
  </div>
</template>

<script>
export default {
name: "MirrorItem",
  props : {
  itemName : "",
    color : ""
  },
  data () {
  return {
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

.mirror-item-text {
  transform: rotate(90deg);
  visibility: hidden;
}

.m-orange {
  background-color: darkorange;
  border: saddlebrown 1px solid;
}
.m-green {
  background-color: darkolivegreen;
  border: darkslategrey 1px solid;
}
</style>
