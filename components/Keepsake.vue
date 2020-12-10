<template>
<div style="display: inline-block">
  <img  :alt="`${keepsakeName}`" :src="require(`~/assets/Keepsakes/${keepsakeImg}`)"/>
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

</style>
