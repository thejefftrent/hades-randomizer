<template>
  <div>
    <h3>Pact Of Punishment</h3>
    <b-form-input id="range-1" v-model="heatBudget" type="range" min="0" max="50"></b-form-input>
    <div class="mt-2">Heat Amount: {{ heatBudget }}</div>
    <HeatItem v-bind:heat-level="m.amount" v-bind:heat-name="m.name" v-for="m in heatItems" :key="heatItems.name"> </HeatItem>
  </div>
</template>

<script>
import hades from '~/assets/data.json';
export default {
name: "Heat",
  model: {
  event: 'change-budget',
    prop : 'heatBudget'
  },
  props : {
  heatItems : Array
  },
  data () {
  return {
    heatBudget : 0
  }

  },
  methods : {

  },
  watch : {
    heatBudget:  {
      immediate: true,
      handler (newVal, oldVal) {
        this.$emit("change-budget", this.heatBudget)
      }
    }
  }

}
</script>

<style scoped>

</style>
