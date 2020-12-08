<template>
  <div>
    <p>{{mirrorItems}}</p>
<!--    <MirrorItem v-for="m in mirrorItems" :key="mirrorItems.name"> </MirrorItem>-->
  </div>
</template>

<script>
import hades from "~/assets/data.json"
export default {
name: "Mirror",
  props : {
    mirrorItems: [{color: 'm-green',name: "testing"}]
  },
  data () {
    return {
      mirrorItems: this.mirrorItems,
    }
  }
}
</script>

<style scoped>

</style>
