<template>
<div style="display: inline-block">
  <img class="keepsake-img"  :alt="`${keepsakeName}`" :src="require(`~/assets/Keepsakes/${keepsakeImg}`)"/>
  <p>{{keepsakeName}}</p>
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
  height: 180px;
  width: 180px;
  object-fit: none;
  display: inline-block;
}
</style>
