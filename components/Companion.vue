<template>
  <div style="display: inline-block">
    <img :alt="`${companionName}`" :src="require(`~/assets/Companions/${companionImg}`)"/>
    <p>{{companionName}}</p>
  </div>
</template>

<script>
export default {
  name: "Companion",
  props : {
    companionName: String,
    companionImg: String
  }
}
</script>

<style scoped>

</style>
