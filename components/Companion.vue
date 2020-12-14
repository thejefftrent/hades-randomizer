<template>
  <div style="display: inline-block">
    <img v-b-tooltip.hover :title="companionName" class="companion-img" :alt="`${companionName}`" :src="require(`~/assets/Companions/${companionImg}`)"/>
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
.companion-img {
  height: 180px;
  width: 180px;
  object-fit: contain;
  display: inline-block;
}
</style>
