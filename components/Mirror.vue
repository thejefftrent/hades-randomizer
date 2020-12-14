<template>
  <div>
    <h3>Mirror</h3>
    <MirrorItem v-b-tooltip.hover :title="m.name" v-bind:color="m.color" v-bind:name="m.name" v-for="m in mirrorItems" :key="mirrorItems.name"> </MirrorItem>
  </div>
</template>

<script>
import hades from "~/assets/data.json"
export default {
name: "Mirror",
  props : {
    mirrorItems: Array
  },
  data () {
    return {
    }
  }
}
</script>

<style scoped>

</style>
