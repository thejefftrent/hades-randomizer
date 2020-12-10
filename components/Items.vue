<template>
<div>
<!--  <b-form-input id="range-1" v-model="heatBudget" type="range" min="1" max="4"></b-form-input>-->
  <p class="mt-2">Keepsakes: {{ 0 }}</p>
  <Companion v-bind:companion-img="companionImg" v-bind:companion-name="companionName"/>
  <Keepsake v-bind:keepsake-name="m.name" v-bind:keepsake-img="m.img" v-for="m in keepsakes" :key="keepsakes.name"> </Keepsake>
</div>
</template>

<script>
import Companion from "@/components/Companion";
import Keepsake from "@/components/Keepsake";
export default {
  name: "Items",
  components: {Keepsake, Companion},
  props : {
    itemRolls: Object
  },
  data () {
    return {
      companionName: this.itemRolls.companion.companionName,
      companionImg: this.itemRolls.companion.companionImg,
      keepsakes: this.itemRolls.keepsakes
    }
  },
  watch : {
    itemRolls : {
      immediate: true,
      handler (newVal, oldVal) {
        this.companionName = newVal.companion.companionName;
          this.companionImg = newVal.companion.companionImg;
          this.keepsakes = newVal.keepsakes;
      }
    }
  }
}
</script>

<style scoped>

</style>
