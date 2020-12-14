<template>
<div style="display: inline-block">
  <img v-b-tooltip.hover :title="keepsakeName" class="keepsake-img"  :alt="`${keepsakeName}`" :src="require(`~/assets/Keepsakes/${keepsakeImg}`)"/>
</div>
</template>

<script>
export default {
name: "Keepsake",
  props: {
  keepsakeName: String,
    keepsakeImg: String
  }
}
</script>

<style scoped>
.keepsake-img {
  height: 100px;
  width: 100px;
  object-fit: contain;
  display: inline-block;
}
</style>
