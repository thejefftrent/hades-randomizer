<template>
  <div>
    <MirrorItem v-bind:color="m.color" v-bind:name="m.name" v-for="m in mirrorItems" :key="mirrorItems"> </MirrorItem>
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
      mirrorItems: this.mirrorItems,
    }
  }
}
</script>

<style scoped>

</style>
